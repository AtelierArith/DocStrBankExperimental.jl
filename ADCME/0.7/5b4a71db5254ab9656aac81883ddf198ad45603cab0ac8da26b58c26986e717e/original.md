```
wgan_stable(gan::GAN, λ::Float64)
```

Returns the discriminator and generator loss for the Wasserstein GAN loss with penalty parameter $\lambda$

The objective function is 

$$
L = E_{\tilde x\sim P_g} [D(\tilde x)] - E_{x\sim P_r} [D(x)] + \lambda E_{\hat x\sim P_{\hat x}}[(||\nabla_{\hat x}D(\hat x)||^2-1)^2]
$$
