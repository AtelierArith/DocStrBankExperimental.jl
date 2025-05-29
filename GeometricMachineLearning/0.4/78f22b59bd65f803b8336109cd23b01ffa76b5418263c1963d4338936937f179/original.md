```
SymplecticAutoencoder(full_dim, reduced_dim)
```

Make an instance of `SymplecticAutoencoder` for dimensions `full_dim` and `reduced_dim`.

# The architecture

The symplectic autoencoder architecture was introduced in [brantner2023symplectic](@cite). Like any other autoencoder it consists of an *encoder* $\Psi^e:\mathbb{R}^{2N}\to\mathbb{R}^{2n}$ and a *decoder* $\Psi^d:\mathbb{R}^{2n}\to\mathbb{R}^{2N}$ with $n\ll{}N$. These satisfy the following properties: 

$$
\begin{aligned}
    \nabla_z\Psi^e\mathbb{J}_{2N}(\nabla_z\Psi^e\mathbb{J}_{2N})^T = \mathbb{J}_{2n} & \quad\text{and} \\
    (\nabla_\xi\Psi^d)^T\mathbb{J}_{2N}\nabla_\xi\Psi^d = \mathbb{J}_{2n}. & 
\end{aligned}
$$

Because the decoder has this particular property, the reduced system can be described by the Hamiltonian $H\circ\Psi^d$: 

$$
\mathbb{J}_{2n}\nabla_\xi(H\circ\Psi^d) = \mathbb{J}_{2n}(\nabla_\xi\Psi^d)^T\nabla_{\Psi^d(\xi)}H = \mathbb{J}_{2n}(\nabla_\xi\Psi^d)^T\mathbb{J}_{2N}^T\mathbb{J}_{2N}\nabla_{\Psi^d(\xi)}H = (\nabla_\xi\Psi^d)^+X_H(\Psi^d(\xi)),
$$

where $(\nabla_\xi\Psi^d)^+$ is the *symplectic inverse* of $\nabla_\xi\Psi^d$ (for more details see the docs on the [`AutoEncoder`](@ref) type).

# Arguments

Besides the required arguments `full_dim` and `reduced_dim` you can provide the following keyword arguments:

  * `n_encoder_layers::Integer = 4`: The number of layers in one encoder block.
  * `n_encoder_blocks::Integer = 2`: The number of encoder blocks.
  * `n_decoder_layers::Integer = 1`: The number of layers in one decoder block.
  * `n_decoder_blocks::Integer = 3`: The number of decoder blocks.
  * `sympnet_upscale::Integer = 5`: The *upscaling dimension* of the GSympNet. See [`GradientLayerQ`](@ref) and [`GradientLayerP`](@ref).
  * `activation = tanh`: The activation in the gradient layers.
  * `encoder_init_q::Bool = true`: Specifies if the first layer in each encoder block should be of $q$ type.
  * `decoder_init_q::Bool = true`: Specifies if the first layer in each decoder block should be of $p$ type.
