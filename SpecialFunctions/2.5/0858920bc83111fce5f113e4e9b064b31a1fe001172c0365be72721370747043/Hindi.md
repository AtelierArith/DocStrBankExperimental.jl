```
beta_inc(a, b, x, y=1-x)
```

एक ट्यूपल लौटाएं $(I_{x}(a,b), 1-I_{x}(a,b))$ जहाँ $I_{x}(a,b)$ नियमितीकृत अधूरा बीटा फ़ंक्शन है जिसे इस प्रकार दिया गया है

$$
I_{x}(a,b) = \frac{1}{B(a,b)} \int_{0}^{x} t^{a-1}(1-t)^{b-1} \mathrm{d}t,
$$

जहाँ $B(a,b) = \Gamma(a)\Gamma(b)/\Gamma(a+b)$।

बाहरी लिंक: [DLMF 8.17.1](https://dlmf.nist.gov/8.17.1), [Wikipedia](https://en.wikipedia.org/wiki/Beta_function#Incomplete_beta_function)

और देखें: [`beta_inc_inv`](@ref)
