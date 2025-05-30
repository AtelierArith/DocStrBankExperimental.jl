```
expintx(z)
expintx(ν, z)
```

स्केल्ड एक्सपोनेंशियल इंटीग्रल की गणना करता है

$$
\exp(z) \operatorname{E}_\nu(z) = e^z \int_1^\infty \frac{e^{-zt}}{t^\nu} \mathrm{d}t.
$$

यदि $\nu$ निर्दिष्ट नहीं किया गया है, तो $\nu = 1$ का उपयोग किया जाता है। मनमाना जटिल $\nu$ और $z$ समर्थित हैं।

और देखें: [`expint(ν, z)`](@ref SpecialFunctions.expint)
