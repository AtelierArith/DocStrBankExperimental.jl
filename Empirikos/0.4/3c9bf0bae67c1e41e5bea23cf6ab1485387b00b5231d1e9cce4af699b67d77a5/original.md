```
cf(::LinearEBayesTarget, t)
```

The characteristic function of $L(\cdot)$, a `LinearEBayesTarget`, which we define as follows:

For $L(\cdot)$ which may be written as $L(G) = \int \psi(\mu)dG\mu$ (for a measurable function $\psi$) this returns the Fourier transform of $\psi$ evaluated at t, i.e., $\psi^*(t) = \int \exp(it x)\psi(x)dx$. Note that $\psi^*(t)$ is such that for distributions $G$ with density $g$ (and $g^*$ the Fourier Transform of $g$) the following holds:

$$
L(G) = \frac{1}{2\pi}\int g^*(\mu)\psi^*(\mu) d\mu
$$
