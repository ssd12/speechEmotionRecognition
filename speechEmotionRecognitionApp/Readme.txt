Speech Emotion Recognition App Readme

App Directory Structure:

speechEmotionRecognitionApp
- Views
	- LaunchScreen.storyboard
	- Main.storyboard
	- CustomButton.swift
- Models
	- words_array.json
	- words_idf.json
	- tfidf_svm.swift
	- AnalyzedResults.swift
	- SpeechToText.swift
	- Recording.swift
- Controllers
	- MainNavigiationController.swift
	- ResultsViewController.swift
	- ViewController.swift



1. Overview:
The speech emotion recognition app allows user to have their speech
classified into different emotion categories. The application transcribes user
Speech from the phone mic into text, and then this text is classified by a support vector machine.

2. App Architecture

	The application uses a MVC architecture. There are three models and three controllers. The main controller (ViewController.swift) allows the user to start and stop his or her recording, and to start text analysis. The second controller (ResultsViewController.swift) is responsible for passing the analyzed results from  the AnalyzedResults model. Lastly, the third controller (MainNavigationController.swift) is used to managed navigation between the other two controllers. 
There are three models- one for recording the text (Recording.swift), a second for speech to transcription from mp3 clips (SpeechToText.swift), and a third for classifying the text based on emotion categories (AnalyzedResults.swift).

3. SVM classifier

	The training data for the SVM classifier is the CrowdFlower/Figure 8 Sentiment Analysis: Emotion in Text dataset (link: https://www.figure-eight.com/data-for-everyone/). This dataset contains 10,000 tweets that are labeled with a corresponding emotion/sentiment. There are 13 emotion categories. The crowd flower dataset undergoes feature engineering via tf-idf. The model is implemented in python using the scikit-learn library. Once it is trained, it is converted into a CoreML model which is imported into the iOS application. 

The CoreML model is fed an input of user transcribed text that has its features extracted via tf-idf.

4. Usage Instructions:

	i). After starting the app, the main screen will show up. There are three buttons- Record, Stop, and Analyze. There is a large white box in the middle of the application- this box will display user transcribed text once recording begins. When the app is started, the box has some filler text that is eventually replaced with user text.

	ii). To begin transcription, press the record button. An alert will popup notifying the user that he or she has started recording. Once the alert is closed, the user can talk and see his or her speech in text format. 

	iii). During recording, if the user presses the Analyze button- another alert will popup notifying the user that they cannot analyze the speech until the recording is finished. In order to analyze the speech, the user must press the Stop button first, and then click on the Analyze button.

	iv). After clicking the Analyze button, the application will transition to the results page that displays probabilities for all the emotion category. The category with the highest probability will be used as the classification. 


