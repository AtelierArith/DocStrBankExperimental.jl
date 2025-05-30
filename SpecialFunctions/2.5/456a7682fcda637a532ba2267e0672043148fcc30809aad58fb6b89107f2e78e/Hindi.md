```
erf(x)
```

$ x $ का त्रुटि फ़ंक्शन की गणना करें, जिसे परिभाषित किया गया है

$$
\operatorname{erf}(x) = \frac{2}{\sqrt{\pi}} \int_0^x \exp(-t^2) \; \mathrm{d}t
\quad \text{के लिए} \quad x \in \mathbb{C} \, .
$$

बाहरी लिंक: [DLMF 7.2.1](https://dlmf.nist.gov/7.2.1), [Wikipedia](https://en.wikipedia.org/wiki/Error_function).

देखें: [`erfc(x)`](@ref erfc), [`erfcx(x)`](@ref erfcx), [`erfi(x)`](@ref erfi), [`dawson(x)`](@ref dawson), [`erfinv(x)`](@ref erfinv), [`erfcinv(x)`](@ref erfcinv).

# द्वारा कार्यान्वयन

  * `Float32`/`Float64`: C मानक गणित पुस्तकालय   [libm](https://en.wikipedia.org/wiki/C_mathematical_functions#libm).
  * `BigFloat`: बहु-परिशुद्धता फ्लोटिंग-पॉइंट के लिए C पुस्तकालय [MPFR](https://www.mpfr.org/)
