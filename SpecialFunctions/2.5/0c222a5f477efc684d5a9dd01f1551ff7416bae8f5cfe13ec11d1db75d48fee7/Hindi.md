```
gamma_inc_asym(a, x, ind)
```

$$
P(a,x)
$$

की गणना करें जो कि निम्नलिखित आसिम्प्टोटिक विस्तार द्वारा दी गई है:

$$
R(a,x)/a * (1 + \sum_{n=1}^{N-1}(a_{n}/x^{n} + \Theta _{n}a_{n}/x^{n}))
$$

जहाँ `R(a,x) = rgammax(a,x)` है। इसका उपयोग तब किया जाता है जब `1 <= a <= BIG` और `x >= x0`।

बाहरी लिंक: [DLMF 8.11.2](https://dlmf.nist.gov/8.11.2)

और देखें: [`gamma_inc(a,x,ind)`](@ref SpecialFunctions.gamma_inc)
