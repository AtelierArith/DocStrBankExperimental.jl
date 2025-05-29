```
spectrum(env::AbstractGaussianEnvelope)
```

ガウス関数は[シュワルツ空間](https://en.wikipedia.org/wiki/Schwartz_space)に属します。つまり、フーリエ変換の下で同じ空間にマッピングされる関数です。言い換えれば、ガウス関数のフーリエ変換はガウス関数です：

$$
\exp(-\alpha t^2) \leftrightarrow
\frac{1}{\sqrt{2\alpha}}
\exp\left(-\frac{\omega^2}{4\alpha}\right).
$$

上記と比較すると、スペクトル標準偏差は

$$
\Omega = \sqrt{2\alpha} = \frac{2\sqrt{\ln 2}}{\tau},
$$

そして、スペクトル領域におけるガウス関数は次のようになります：

$$
E(\omega) =
\frac{E_0\tau}{2\sqrt{\ln 2}}
\exp\left[-\frac{(\omega\tau)^2}{8\ln2}\right].
$$
