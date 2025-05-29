```
PSDLayer(input_dim, output_dim)
```

Make an instance of `PSDLayer`.

This is a PSD-like layer used for symplectic autoencoders.  One layer has the following shape:

$$
A = \begin{bmatrix} \Phi & \mathbb{O} \\ \mathbb{O} & \Phi \end{bmatrix},
$$

where $\Phi$ is an element of the Stiefel manifold $St(n, N)$.
