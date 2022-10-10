# Stress-Detection-using-Facial-Recognition

Can stress be detected? 
A general problem in stress detection is that the measurement of emotion is difficult. It is difficult to detect and report on these subjective states accurately given their short duration. There is also a possibility that some emotional experiences may be unconscious, which makes them impossible to measure. However, there has been research that has suggested possible connections between emotions and emotional states, such as depression, anxiety and stress. Negative emotions appear to be a sufficient, although not a necessary cause of physiological responses to stressors in laboratory stress studies. Stress was linked to increased negative emotions, such as anger, while positive emotions, such as happiness, were linked to an increased physiological ability to recover from chronic stress. 
 
How can stress be detected? 
Most of the time, traditional stress detection systems rely on psychological questionnaires that can be very subjective. Other systems demand wearable sensors that cannot realize contact-free measurement. With the fast progress of data collection and analysis techniques, we are now able to detect human stress based on image sequences captured from a webcam. This system offers us a few benefits. Firstly, it is easy-to-use and more convenient in places like hospitals, schools, et cetera. Secondly, it can reach mass audience at a lower cost. 
 
Which features indicate stress? 
There are several studies reporting that facial expressions can provide insights into the identification of stress. Most of the existing work in the literature focuses on extracting facial signs such as mouth activity, head motion, blink rate, pupil dilation and eye movements from different facial regions. 
Mouth activities have been found to correlate with signs of several conditions: depressed people smile less, while those overwhelmed with fatigue yawn more. To obtain these results, two features have been extracted, such as mouth openings and mouth deformations. 
Another research shows that although eye-blinking is a semi-voluntary action, it is affected by one’s emotional states such as arousal or stress. It was observed that eye blinks appear to be significantly increased in specific stressful tasks. Additionally, it was reported that there are four types of eye blink patterns categorized according to the inter-blink interval behavior. 
 
 
 Scenarios  
The stress detection system can be used by: 
drivers to detect stress on the road and prevent car accidents; 
doctors to develop a better understanding on their patients’ mental state and help the patients accordingly;  
school teachers to monitor students’ mental state and help the students accordingly; 
(office) researchers to analyse during which hours and in what environments people can function the most efficient in; 
and any person who has mental issues, which include stress, to awaken awareness and provide them more control over the situation and the ability to seek professional help.  
 
Face recognition 
For the face recognition program, I have used the MATLAB cascade object detector. Firstly, the program takes snapshots from the web camera every X seconds. Each image, the input, should be normalized: the face should be located and then cropped. Cropping the image helps us obtain the relevant part of the image for the system. It can also recognize facial parts: the mouth and eyes. These facial parts have also been normalized. Lastly, each cropped image is saved as a file to the current folder, so that they can be used for image processing and classification.  
 
 
% Face detection using Viola-Jones algorithm via MATLAB Cascade Object Detector 
FDetect = vision.CascadeObjectDetector;  
 
% Return bounding box values based on number of objects  
BB = step(FDetect,I); 
 
 
Features 
Stress can be detected through various features on the face. I thought it would be the best to detect stress through excessive blinking, as this seems to be a feature that does not commonly appear with other emotions. A blink can be seen as a rapid closing and opening of the eye. By detecting the number of blinks during one minute and then comparing the blink rate to the average blinking rate in normal circumstances, excessive blinking can be determined. The average blinking rate for humans in normal circumstances, is calculated to be 14 to 17 times a minute.  
 
Iris detection 
Since there are circular objects in the eye, which are the iris and the pupil, we can use these for our classification method of detecting if the eye is open, the iris is detected, or closed, no iris is detected. With our datasets we can determine the values which point out to open eyes and use this for our classifier.  


Classifiers 
The datasets can be used to determine the values which point out to open eyes and use this for our classifier. 
If there is a circular object, the iris, then the eye is open.  
If there is no circular object, then the eye is closed.  
Since facial recognition will take place before the classifiers, it means that if there is no one sitting in the driver’s seat or the driver is facing away, the facial recognition will not recognize eyes and thus the classifiers cannot be executed. This excludes the chance of the classifier detecting closed eyes when there are no eyes to be detected in the first place.  
If the then calculated blinking rate is much higher than the average, the system will give a signal that stress has been detected.  
 
Results 
The facial recognition function of the system can be inaccurate sometimes. This is usually because it can detect the face almost all of the time, but not the eyes. Due to poor lighting, the system can either not detect the eyes at all or detects two pair of eyes; one of them being the actual eyes of the user and the other being imaginary eyes, such as random objects in the image or the nose holes of a user. When more than one pair of eyes gets detected, the system returns an error because it is supposed to normalise on one pair of eyes on the image only. The accuracy of the facial recognition function is difficult to determine, as this mistake happens randomly. If it does happen, it will happen a few times in a row, because of poor lighting or poor camera placement. However, when the environment is fine and the camera is set up properly, the function is very accurate.  
