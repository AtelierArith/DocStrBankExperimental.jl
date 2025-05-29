```
GradientLayerQ(n, upscaling_dimension, activation)
```

Make an instance of a gradient-$q$ layer.

The gradient layer that changes the $q$ component. It is of the form: 

$$
\begin{bmatrix}
        \mathbb{I} & \nabla{}V \\ \mathbb{O} & \mathbb{I} 
\end{bmatrix},
$$

with $V(p) = \sum_{i=1}^Ma_i\Sigma(\sum_jk_{ij}p_j+b_i)$, where $\mathtt{activation} \equiv \Sigma$ is the antiderivative of the activation function $\sigma$ (one-layer neural network). We refer to $M$ as the *upscaling dimension*. 

Such layers are by construction symplectic.
