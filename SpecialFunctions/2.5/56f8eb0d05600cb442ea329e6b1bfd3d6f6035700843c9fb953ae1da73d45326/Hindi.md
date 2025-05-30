```
gamma_inc_temme(a, x, z)
```

$$
P(a,x)
$$

की गणना करें जो टेम के विस्तार द्वारा दी गई है:

$$
1/2 * \operatorname{erfc}(\sqrt{y}) - e^{-y}/\sqrt{2\pi a} ⋅ T(a,\lambda)
$$

जहाँ

$$
T(a,\lambda) = \sum_{0}^{N} c_{k}(z)a^{-k}
$$

यह मुख्य रूप से उस क्षेत्र के पास समस्या को हल करता है जब `a ≈ x` होता है और यह न्यूनतम अधिकतम अनुमान का एक निम्न सटीकता संस्करण है।

बाहरी लिंक: [DLMF 8.12.8](https://dlmf.nist.gov/8.12.8)

देखें: [`gamma_inc(a,x,ind)`](@ref SpecialFunctions.gamma_inc) ```
