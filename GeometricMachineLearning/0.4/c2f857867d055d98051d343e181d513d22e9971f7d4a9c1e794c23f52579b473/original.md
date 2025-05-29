```
GradientLayerP(n, upscaling_dimension, activation)
```

Make an instance of a gradient-$p$ layer.

The gradient layer that changes the $p$ component. It is of the form: 

$$
\begin{bmatrix}
        \mathbb{I} & \mathbb{O} \\ \nabla{}V & \mathbb{I} 
\end{bmatrix},
$$

with $V(p) = \sum_{i=1}^Ma_i\Sigma(\sum_jk_{ij}q_j+b_i)$, where $\mathtt{activation} \equiv \Sigma$ is the antiderivative of the activation function $\sigma$ (one-layer neural network). We refer to $M$ as the *upscaling dimension*. 

Such layers are by construction symplectic.
