# miniproject-PMML

---
## Comparative Study of Four Different CNN Architecture

#### Four distinct CNN models were implemented and trained:


1. Baseline CNN (PaperCNN): An implementation of the architecture described in the research paper, featuring two convolutional layers, two max-pooling layers, and three fully-connected layers. Key parameters included a 3x3 convolution kernel with a stride of 3 and a 2x2 max-pooling kernel. The model was trained for 20 epochs using an SGD optimizer with momentum.




2. CBAM-CNN: An enhanced version of the baseline model incorporating the Convolutional Block Attention Module (CBAM) after each convolutional layer to refine feature maps.


3. Residual-CNN: A variant that replaces standard convolutional layers with residual blocks, a concept mentioned in the paper's introduction to improve training in deeper networks.

4. ThreeConvCNN: A deeper version of the baseline model with an additional convolutional layer.

All models were trained on the same 90/10 training-validation split of the CIFAR-10 training data and evaluated on the official test set. Performance was measured by test accuracy, number of parameters, and inference time per image.

---

#### Key Observations

1. Residual Connections Provide the Best Performance-Efficiency Balance: The Residual-CNN delivered the highest accuracy while only being marginally more complex and slower than the baseline. This demonstrates that its architectural design effectively improves the network's learning capability without significant computational cost.

2. The Baseline PaperCNN is a Strong and Efficient Model: The PaperCNN, which implements the architecture from the research paper, stands out as the most efficient model. It has the fewest parameters (36,618) and the fastest inference time (0.007 ms/image), while achieving a test accuracy (62.54%) that is very close to the best-performing model. This makes it an excellent choice when computational resources are limited.

3. Attention (CBAM) Did Not Improve Performance in This Case: The CBAM-CNN resulted in the lowest accuracy (58.65%) while being the slowest model by a significant margin (0.020 ms/image). This suggests that for this specific, relatively shallow architecture, the added complexity of the attention mechanism did not translate into better performance and introduced unnecessary computational overhead.

4. Simply Adding Depth (ThreeConvCNN) is Ineffective: The ThreeConvCNN illustrates that naively increasing network depth and parameters does not guarantee better results. Despite having over four times the parameters of the baseline model, its accuracy (60.56%) was lower than both the PaperCNN and Residual-CNN. This highlights that intelligent architectural choices, like residual connections, are more crucial for performance than just adding more layers.

---

#### Results and Analysis
The experimental results show that the custom CNN architectures were effective for the image classification task. The Residual-CNN achieved the highest test accuracy at 63.36%, slightly outperforming the baseline PaperCNN which recorded an accuracy of 62.54%. This supports the paper's suggestion that residual connections can improve model performance. The 

CBAM-CNN model, despite its attention mechanism, yielded a lower accuracy of 58.65%, while the deeper ThreeConvCNN achieved 60.56% accuracy.

In terms of efficiency, the baseline PaperCNN was the fastest in inference time at approximately 0.007 ms per image. The Residual-CNN, with a slightly higher parameter count (39,050 vs. 36,618), had a comparable inference time of 0.012 ms per image.

The accuracy achieved by the baseline model in this implementation (62.72% before the final run, 62.54% in the final comparison) is lower than the near 80% accuracy reported in the paper. This discrepancy could be attributed to differences in specific framework implementations, hardware, or minor variations in training hyperparameters not detailed in the paper. However, the implemented model still demonstrated a significant improvement over traditional methods like SVM and KNN, aligning with the paper's primary conclusion. For instance, the accuracy for classes with distinct features like "airplane" and "ship" was high, while it was lower for more ambiguous classes like "cat," a finding consistent with the paper's analysis.

---


