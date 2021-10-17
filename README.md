# Multi-label-classification

## Team members
* Tran Cong Thinh
* Nguyen Hoang Phuc
* Chau Hoang Tu
* Vu Thi Quynh Nga

## 2 stages of our solution:
1. Preprocessing the input data
2. building the model

## 1. First stage

Step 1: Resize the images into the size of 128x128

Step 2: Enhance the images' quality by using a trained autoencoder model

![image](https://user-images.githubusercontent.com/68393604/137612249-01147c53-0957-4bc1-8686-679dd0182b76.png)

![image](https://user-images.githubusercontent.com/68393604/137612243-a66e42f5-46db-46ea-a0ad-b93507df1762.png)

Step 3: Augment images by using Albumentations’ s functions
After using an autoencoder model, we saw an increase in 2 percent in the test accuracy (from 96 → more than 98)

Step 3: Augment images by using Albumentations’ s functions 
We used 5 below Albumentations’ s functions to augment our image dataset
* OpticalDistortion
* ColorJitter
* Rotate
* RandomShadow
* Cutout

Step 4: Convert labels to fit with the multi-label model

Because there are 7 unique labels according to the given json file, and a maximum of 5 different attributes in one image, we decide to convert the labels in a special way to fit with the multi-label model.

* The 7 unique labels : “straight” , ”left”, “right”, “entrance to the ring”, “slightly to the left”, “slightly on the right”, “to the right followed by the left turn”.
* The 5 attributes representing for the maximum of 5 lanes in an image.

![image](https://user-images.githubusercontent.com/68393604/137613928-7860b45b-f90f-48c9-95ea-8088eecd7af1.png)

As you can see on the screen, this is a 5x7 matrix representing the label “left, right+straight” on the dataset. Since the maximum of attributes/lanes in an image is 5, there are 5 rows in this matrix. Similarly, as there are 7 types of basic attributes in the json file, this matrix also has 7 columns. 

After that, we flatten the matrix to fix it in our multi-label model.

![image](https://user-images.githubusercontent.com/68393604/137613934-3e235c0c-2063-448e-8665-efcdfa9d972d.png)


## 2. Second stage

In the second stage of the solution, we train our multi-label model. Below is the structure of our best model so far. 

![image](https://user-images.githubusercontent.com/68393604/137613817-4aba8cd5-4a5d-4592-a515-a68cd477802e.png)

Attention to our output layer, which has 35 nodes and a sigmoid activation, not softmax. 

After many trials-and-errors, we choose to use the ROC-AUC score since the normal accuracy metrics did not work well in this case. We also use binary cross-entropy loss to train this model. 


## 3. Deployment


## 4. Model's strengths

## 5. Obstacles


## 6. Future vision
