```
NeuralNetworkKernel()
```

Kernel of a Gaussian process obtained as the limit of a Bayesian neural network with a single hidden layer as the number of units goes to infinity.

# Definition

Consider the single-layer Bayesian neural network $f \colon \mathbb{R}^d \to \mathbb{R}$ with $h$ hidden units defined by

$$
f(x; b, v, u) = b + \sqrt{\frac{\pi}{2}} \sum_{i=1}^{h} v_i \mathrm{erf}\big(u_i^\top x\big),
$$

where $\mathrm{erf}$ is the error function, and with prior distributions

$$
\begin{aligned}
b &\sim \mathcal{N}(0, \sigma_b^2),\\
v &\sim \mathcal{N}(0, \sigma_v^2 \mathrm{I}_{h}/h),\\
u_i &\sim \mathcal{N}(0, \mathrm{I}_{d}/2) \qquad (i = 1,\ldots,h).
\end{aligned}
$$

As $h \to \infty$, the neural network converges to the Gaussian process

$$
g(\cdot) \sim \mathcal{GP}\big(0, \sigma_b^2 + \sigma_v^2 k(\cdot, \cdot)\big),
$$

where the neural network kernel $k$ is given by

$$
k(x, x') = \arcsin\left(\frac{x^\top x'}{\sqrt{\big(1 + \|x\|^2_2\big) \big(1 + \|x'\|_2^2\big)}}\right)
$$

for inputs $x, x' \in \mathbb{R}^d$.[^CW]

[^CW]: C. K. I. Williams (1998). Computation with infinite neural networks.
