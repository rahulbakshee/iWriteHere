### Problem Statement
In-Store analytics is very important when it comes to ->
- efficiently managing the product placements.
- optimizing store operations.
- how customers feel when they are inside the store.
- how customers feel when talking to a customer representative(rep).
- customers' overall shopping experience.
- personalizing marketing content 
- recommending relevant products
- etc.

Companies/Retailers have been using image/video analysis of in-store customers' interactions to get insights for the above tasks. But, most systems are batch-mode and not real-time. The primary use of real-time is to know instantly how the customer feels and change your course of action based on that. 

> read this on [github pages](https://rahulbakshee.github.io/iWriteHere/2022/03/08/RealTime-InStore-Sentiment-Analysis-RISA.html) 

### Approach
In this project we will build a Real-Time In-Store Sentiment Analysis system(RISA) to know more about customer's sentiments while they are inside the store. After generating real-time insights of customer's sentiments, the store owner can work on cutomer loyalty and engagement programs. 

- Step 1 - Collect facial data of customers from images/videos using camera feed/Raspberry Pi etc.
- Step 2 - The facial crops are then classified as one of the categories (Happy, Sad, Neutral etc.) for each person.

![risa-diag]({{ '/images/2022-03-08-RISA-diag.png' | relative_url }})
<img src="/images/2022-03-08-RISA-diag.png" style="width:600px;height:600;">
Figure 1: This figure shows High level System Design of Real-Time In-Store Sentiment Analysis [RISA]



### Technical Solution
We have prototyped it as a two step process a **Face Detection** followed by **Facial Expression Recognition**. `The main thing to notice here is we are never going to store customer's information like facial crop etc. to keep user's identity confidential and maintain privacy. We only store the overall aggregated emotion insights without any personal identity of the user.`

To achieve the Face Detection , there are many methods available and each has pros and cons in terms of accuracy, latency etc.:
- [HAAR Cascade Classifier from OpenCV](https://docs.opencv.org/3.4/db/d28/tutorial_cascade_classifier.html)
- MTCNN (Facenet-pytorch)
- [DLib(HOG/CNN)](http://dlib.net/) / [face_recognition](https://github.com/ageitgey/face_recognition)
- [MediaPipe Face Detection](https://google.github.io/mediapipe/solutions/face_detection.html)
- etc.

For Facial Expression Recognition, we can use any classifier:
- Pretrained classifiers
- Train from scratch


Whatever we choose, we must have low latency inference as we would like to generate real-time insights. 


There are various datasets avilable for use:
- FER-2013
- FER+ 
- CK+ (extended Cohn-Kanade).
- etc.

![emotions]({{ '/images/2022-03-08-all-emotions.png' | relative_url }})
<img src="/images/2022-03-08-all-emotions.png" style="width:600px;height:600;">

Figure 2: This figure shows real-time distribution of emotions per customer present in store


### Conclusion
Using this product, one can easily understand the overall emotion of in-store customers in real-time and work on optimizing the store performance and customer engagements.

