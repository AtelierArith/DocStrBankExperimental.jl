```
gamma_inc_cf(a, x, ind)
```

$$
P(a,x)
$$

की गणना निरंतर भिन्न विस्तार द्वारा की जाती है:

$$
R(a,x) \cdot \cfrac{1}{1-\cfrac{z}{a+1+\cfrac{z}{a+2-\cfrac{(a+1)z}{a+3+\cfrac{2z}{a+4-\cfrac{(a+2)z}{a+5+\cfrac{3z}{a+6-\ddots}}}}}}}
$$

जब उपयोग किया जाता है `1 <= a <= BIG` और `x < x0`।

बाहरी लिंक: [DLMF 8.9.2](https://dlmf.nist.gov/8.9.2)

और देखें: [`gamma_inc(a,x,ind)`](@ref SpecialFunctions.gamma_inc)
