```
erfc(x)
```

$$
x
$$

के लिए परिपूरक त्रुटि फ़ंक्शन की गणना करें, जिसे परिभाषित किया गया है

$$
\operatorname{erfc}(x)
= 1 - \operatorname{erf}(x)
= \frac{2}{\sqrt{\pi}} \int_x^\infty \exp(-t^2) \; \mathrm{d}t
\quad \text{के लिए} \quad x \in \mathbb{C} \, .
$$

यह बड़े $x$ के लिए `1-erf(x)` का सटीक संस्करण है।

बाहरी लिंक: [DLMF 7.2.2](https://dlmf.nist.gov/7.2.2), [Wikipedia](https://en.wikipedia.org/wiki/Error_function#Complementary_error_function).

देखें: [`erf(x)`](@ref erf).

# द्वारा कार्यान्वयन

  * `Float32`/`Float64`: C मानक गणित पुस्तकालय   [libm](https://en.wikipedia.org/wiki/C_mathematical_functions#libm).
  * `BigFloat`: बहु-परिशुद्धता फ्लोटिंग-पॉइंट के लिए C पुस्तकालय [MPFR](https://www.mpfr.org/)
