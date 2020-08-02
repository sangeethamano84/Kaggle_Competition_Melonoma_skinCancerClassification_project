# Kaggle_Competition_Melonoma_skinCancerClassification_project

## SIIM-ISIC Melanoma Classification
***Introduction***: Society for Imaging Informatics in Medicine(SIIM)”s joined International Skin Imaging Collaboration(ISIC), to improve melanoma diagnosis competition held on kaggle. 
Skin cancer is the most prevalent type of cancer. Melanoma, specifically, is responsible for 75% of skin cancer deaths, despite being the least common skin cancer. The American Cancer Society estimates over 100,000 new melanoma cases will be diagnosed in 2020. It's also expected that almost 7,000 people will die from the disease.

***The Goal:*** Melanoma Skin cancer is common cancer type and despite beign mostly non malignant, due to high case numbers it's pretty serious diasease and can lead serious cases if not detected, treated in time. It's usually diagnosed by eye for primarily and followed by further clinical analysis if needed. Even though the rares outcome is called melanoma it's the most deadly one, so early detection is pretty important. For this task using computer aided diagnosis might be helpful for primarily steps and early detections. Better detection might save thousands of lives.
This competition might help reaching that goal and I hope it can help people around the world...

***The data:*** Train data has 8 features, 33126 observations and Test data 5 features, 10982 observations.
Image Names, Sex, Age, Anatom Sites, Width/Height of the Images and Targets of:
Current 2020 set with 33k examples including 584 malignant examples,
2017/18-2019 set with 25k examples with 4522 malignant examples,
580 completely new malignant examples coming from Chris Deotte's Malignant TFRecords 15-29
We'll continue by loading metadata we're given. 

Train Dataset Consists Of:
* 1.image name -> the filename of specific image for the train set
* 2.patient_id -> identifies the unique patient
* 3.sex -> gender of the patient
* 4.age_approx -> approx age of the patient at time of scanning
* 5.anatom_site_general_challenge -> location of the scan site
* 6.diagnosis -> information about the diagnosis
* 7.benign_malignant - indicates scan result if it's malignant or benign
* 8.target -> same as above but better for modelling since it's binary
And the next dataset we going to inspect test. It has same features as train set except for scan results, well that's why it's test set right?!

Train Dataset Consists Of:
* 1.image name -> the filename of specific image for the train set
* 2.patient_id -> identifies the unique patient
* 3.sex -> gender of the patient
* 4.age_approx -> approx age of the patient at time of scanning
* 5.anatom_site_general_challenge -> location of the scan site 


***EfficientNet Model:*** This repository contains a Keras (and TensorFlow Keras) reimplementation of EfficientNet, a lightweight convolutional neural network architecture achieving the state-of-the-art accuracy with an order of magnitude fewer parameters and FLOPS, on both ImageNet and five other commonly used transfer learning datasets.
EfficientNets, TensorFlow implementation:

EfficientNets are a family of image classification models, which achieve state-of-the-art accuracy, yet being an order-of-magnitude smaller and faster than previous models. We develop EfficientNets based on AutoML and Compound Scaling. In particular, we first use AutoML Mobile framework to develop a mobile-size baseline network, named as EfficientNet-B0; Then, we use the compound scaling method to scale up this baseline to obtain EfficientNet-B1 to B7.

EfficientNets achieve state-of-the-art accuracy on ImageNet with an order of magnitude better efficiency:

In high-accuracy regime, our EfficientNet-B7 achieves state-of-the-art 84.4% top-1 / 97.1% top-5 accuracy on ImageNet with 66M parameters and 37B FLOPS, being 8.4x smaller and 6.1x faster on CPU inference than previous best Gpipe.

In middle-accuracy regime, our EfficientNet-B1 is 7.6x smaller and 5.7x faster on CPU inference than ResNet-152, with similar ImageNet accuracy.

Compared with the widely used ResNet-50, our EfficientNet-B4 improves the top-1 accuracy from 76.3% of ResNet-50 to 82.6% (+6.3%), under similar FLOPS constraint.

***Hyperparameter tuning:*** To improve the model's performance with your dataset, you can tune the model's hyperparameters. However, fine-tuning through a large classification might be prone to overfit.
Fine-tuning requires importing the graph version with tag set {"train"} in order to operate batch normalization in training mode.

***Learning rate:*** This is the rate at which the neural network weights change between iterations. A large learning rate may cause large swings in the weights, and we may never find their optimal values. A low learning rate is good, but the model will take more iterations to converge. It is a good idea to start low, say at 1e-4. If the training is very slow, increase this value. If your model is not learning, try decreasing learning rate.

***Test Time Augmentation (TTA):*** Data augmentation technique for the test dataset, where multiple augmentaed copies of images in dataset is created with zoom, flip and shifts
* The artificially expanded training dataset can result in a more skillful model, as often the performance of deep learning models continues to scale in concert       with the size of the training dataset
*The model makes prediction for each and then ensemble of the predictions are returned.

***Submission File:*** Submissions are evaluated on area under the ROC curve between the predicted probability and the observed target.
For each image_name in the test set, you must predict the probability (target) that the sample is malignant. The file should contain a header and have the following format:

image_name,target
ISIC_0052060,0.7
ISIC_0052349,0.9
ISIC_0058510,0.8
ISIC_0073313,0.5
ISIC_0073502,0.5
etc.
