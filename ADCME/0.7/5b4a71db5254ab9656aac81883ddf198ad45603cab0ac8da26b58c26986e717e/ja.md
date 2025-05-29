```
wgan_stable(gan::GAN, λ::Float64)
```

Wasserstein GAN損失のペナルティパラメータ$\lambda$に対する識別器と生成器の損失を返します。

目的関数は次の通りです。

$$
L = E_{\tilde x\sim P_g} [D(\tilde x)] - E_{x\sim P_r} [D(x)] + \lambda E_{\hat x\sim P_{\hat x}}[(||\nabla_{\hat x}D(\hat x)||^2-1)^2]
$$
