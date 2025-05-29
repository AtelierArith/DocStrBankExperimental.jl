```
FourierFilterNet(in_dims::Int, out_dims::Int; hidden_dims::Int, num_layers::Int,
                 bandwidth::Real)
```

Multiplicative filter network defined by

$$
\begin{aligned}
z^{(1)} &=g\left(x ; \theta^{(1)}\right) \\
z^{(i+1)} &=\left(W^{(i)} z^{(i)}+b^{(i)}\right) \circ \sin \left(\omega^{(i)} x+\phi^{(i)}\right)\right) \\
f(x) &=W^{(k)} z^{(k)}+b^{(k)}
\end{aligned}
$$

## Keyword Arguments

  * `bandwidth`: The maximum bandwidth of the network. The bandwidth is the sum of each filter's bandwidth.

## Parameters

  * Parameters of the filters:

$$
    W\sim \mathcal{U}(-\frac{ω}{n}, \frac{ω}{n}), \quad b\sim \mathcal{U}(-\pi, \pi),
$$

where `n` is the number of filters.

For a periodic function with period $P$, the Fourier series in amplitude-phase form is

$$
s_N(x)=\frac{a_0}{2}+\sum_{n=1}^N{a_n}\cdot \sin \left( \frac{2\pi}{P}nx+\varphi _n \right)
$$

We have the following relation between the banthwidth and the parameters of the model:

$$
ω = 2πB=\frac{2πN}{P}.
$$

where $B$ is the bandwidth of the network.

## References

[fathony2021multiplicative](@cite)

[lindell2021bacon](@cite)
