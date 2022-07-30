# **Challenge-15 Instructions**
This section divides the Challenge instructions into the following three steps:

  1. Configure the initial robo advisor

  2. Build and test the robo advisor

  3. Enhance the robo advisor with an Amazon Lambda function

## **Step 1: Configure the Initial Robo Advisor**
In this section, you create the robo advisor bot and add an intent with its corresponding slots. To do so, complete the following steps:

  1. Sign in to your AWS Management Console, and then create a new custom Amazon Lex bot (Links to an external site.). Use the following criteria:

    - Bot name: RoboAdvisor
    - Language: English (US)
    - Output voice: Salli
    - Session timeout: 5 minutes
    - Sentiment analysis: No
    - COPPA: No
    - Advanced options: No
    - All other options: The default value

  2. Add a new intent, and name it recommendPortfolio.

  3. Configure sample utterances as follows (you can add more utterances if you want):

    - I want to save money for my retirement
    - I'm {age} and I would like to invest for my retirement
    - I'm {age} and I want to invest for my retirement
    - I want the best option to invest for my retirement
    - I'm worried about my retirement
    - I want to invest for my retirement
    - I would like to invest for my retirement

  4. Create four slots, as the following image specifies:
![15-4-bot-slots](https://user-images.githubusercontent.com/103230949/181870158-40e22942-5214-425f-8848-551023cf65ee.png)

> **IMPORTANT**

Remember to mark all the slots as required, as the following image shows:
![15-4-slots-marked-as-required](https://user-images.githubusercontent.com/103230949/181870171-b712ae43-32da-4f8e-861f-80003a7a903b.png)

  5. Move to the “Confirmation prompt” section, and then set the following messages:

    - Confirm: Thanks, now I will look for the best investment portfolio for you.
    - Cancel: I will be pleased to assist you in the future.

## **Step 2: Build and Test the Robo Advisor**
In this section, you build and test your robo advisor. To do so, complete the following steps:

  1. To build your bot, click the Build button (in the upper-right corner of the page).

  2. When the build finishes, test it in the “Test bot” pane. The following animation shows a sample test conversation:
![15-4-robo-advisor-test-without-lambda](https://user-images.githubusercontent.com/103230949/181870184-807b2be9-73f0-4768-89e7-68ef846473dc.gif)


In the preceding animation, a user starts a dialogue with the robo advisor. The dialogue is as follows:
![dialogue](https://user-images.githubusercontent.com/103230949/181870198-13561adc-11b6-4c29-8e00-88873f636f0d.png)

  3. Record a video or create an animated GIF of the working bot.

## **Step 3: Enhance the Robo Advisor with an Amazon Lambda Function**
In this section, you create an Amazon Lambda function to validate the data that a user supplies during a conversation with the robo advisor. To do so, complete the following steps:

  1. Create a new Lambda function from scratch, and name it recommendPortfolio. Choose Python 3.7 as the runtime programming language.

  2. In the online code editor, delete the AWS-generated default lines of code, and then paste in the provided starter code from ```lambda_function.py```.

  3. Complete the ```recommend_portfolio``` function by adding the following validation rules:

    - The value of **_age_** should be greater than zero and less than 65.
    - The value of **_investment_amount_** should be greater than or equal to 5000.

  4. Complete the starter code so that once the intent is fulfilled, the bot responds with an investment recommendation based on the selected risk level, as follows:

    - None: “100% bonds (AGG), 0% equities (SPY)”
    - Low: “60% bonds (AGG), 40% equities (SPY)”
    - Medium: “40% bonds (AGG), 60% equities (SPY)”
    - High: “20% bonds (AGG), 80% equities (SPY)”

  5. When you finish coding your Lambda function, test it by using the provided test events.

  6. After successfully testing your code, open the Amazon Lex console, and then navigate to the recommendPortfolio bot configuration. Integrate your new Lambda function into the bot by selecting it in the “Lambda initialization and validation” and “Fulfillment” sections.

  7. Build your bot, and then test it with both valid and invalid data for the slots.

  8. Record a video or create an animated GIF of the working bot.
