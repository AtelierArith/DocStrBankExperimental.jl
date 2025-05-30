```
gamma_inc(a,x,IND=0)
```

एक ट्यूपल $(p, q)$ लौटाता है जहाँ $p + q = 1$, और $p = P(a,x)$ अधूरा गामा फ़ंक्शन अनुपात है जिसे इस प्रकार दिया गया है:

$$
P(a,x) = \frac{1}{\Gamma (a)} \int_{0}^{x} e^{-t}t^{a-1} \mathrm{d}t.
$$

और $q = Q(a,x)$ अधूरा गामा फ़ंक्शन अनुपात है जिसे इस प्रकार दिया गया है:

$$
Q(a,x) = \frac{1}{\Gamma (a)} \int_{x}^{\infty} e^{-t}t^{a-1} \mathrm{d}t.
$$

इनके संदर्भ में, निम्न अधूरा गामा फ़ंक्शन $\gamma(a,x) = P(a,x) \Gamma(a)$ है और ऊपरी अधूरा गामा फ़ंक्शन $\Gamma(a,x) = Q(a,x) \Gamma(a)$ है।

`IND ∈ [0,1,2]` सटीकता सेट करता है:

  * `IND=0` का अर्थ है 14 महत्वपूर्ण अंकों की सटीकता,
  * `IND=1` का अर्थ है 6 महत्वपूर्ण अंकों की सटीकता, और
  * `IND=2` का अर्थ है केवल 3 अंकों की सटीकता।

बाहरी लिंक: [DLMF 8.2.4](https://dlmf.nist.gov/8.2.4), [Wikipedia](https://en.wikipedia.org/wiki/Incomplete_gamma_function)

और देखें [`gamma(z)`](@ref SpecialFunctions.gamma), [`gamma_inc_inv(a,p,q)`](@ref SpecialFunctions.gamma_inc_inv)
