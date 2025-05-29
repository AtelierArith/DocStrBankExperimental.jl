```
spectrum(env::AbstractGaussianEnvelope)
```

Gaussians belong to the [Schwartz class](https://en.wikipedia.org/wiki/Schwartz_space), i.e. functions who, under Fourier transform, are mapped back to the same space. That is to say, the Fourier transform of a Gaussian is a Gaussian:

$$
\exp(-\alpha t^2) \leftrightarrow
\frac{1}{\sqrt{2\alpha}}
\exp\left(-\frac{\omega^2}{4\alpha}\right).
$$

Comparing with the above, we find that the spectral standard deviation

$$
\Omega = \sqrt{2\alpha} = \frac{2\sqrt{\ln 2}}{\tau},
$$

and the Gaussian function in the spectral domain is thus

$$
E(\omega) =
\frac{E_0\tau}{2\sqrt{\ln 2}}
\exp\left[-\frac{(\omega\tau)^2}{8\ln2}\right].
$$
