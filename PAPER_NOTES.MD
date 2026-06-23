# Paper Notes: Learning representations by back-propagating errors
**Authors:** David E. Rumelhart, Geoffrey E. Hinton & Ronald J. Williams (1986)

### 1. The Central Claim
The paper asserts that a general-purpose learning procedure called "back-propagation" allows neural networks with intermediate "hidden" layers to learn complex, internal representations. This is a massive leap forward because earlier models, like the standard perceptron, could not map non-linear relationships (like XOR or symmetry) because they lacked hidden units that could learn their own feature representations. By using the chain rule to propagate error derivatives backwards through the network, the hidden units learn to represent important features of the task domain.

### 2. Core Architecture & Algorithm
The architecture is a layered, feed-forward neural network consisting of an input layer, one or more hidden layers, and an output layer.
* **Forward Pass:** The total input to a unit is a linear combination of its inputs and weights: $x_j = \sum_i y_i w_{ji}$. This is passed through a non-linear sigmoid activation function: $y_j = 1 / (1 + e^{-x_j})$.
* **Loss Function:** The network minimizes the total squared error between actual and desired outputs: $E = \frac{1}{2}\sum_c\sum_j (y_{j,c} - d_{j,c})^2$.
* **Backward Pass:** The error is propagated backward using the chain rule to compute the gradient.
* **Weight Update:** Gradient descent is applied with a momentum term to accelerate learning and avoid local minima: $\Delta w(t) = -\epsilon \frac{\partial E}{\partial w(t)} + \alpha \Delta w(t-1)$.

### 3. Dataset, Baseline, and Evaluation Metric
* **Dataset/Task:** The Symmetry Detection Task. The network must detect whether a 1D array of 6 binary inputs is symmetrical about its center.
* **Baseline:** The implicit baseline is the standard Perceptrons convergence procedure, which mathematically fails at this task because it cannot utilize hidden layers. 
* **Metric:** The paper evaluates success based on whether the network can perfectly learn the training cases. For binary outputs, they considered the error to be zero if the target "1" had an output > 0.8, and a target "0" had an output < 0.2.
