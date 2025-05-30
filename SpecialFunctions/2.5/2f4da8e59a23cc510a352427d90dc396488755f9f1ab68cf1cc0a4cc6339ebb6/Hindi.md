```
erfcx(x)
```

$$
x
$$

के लिए परिभाषित स्केल्ड अनुपूरक त्रुटि फ़ंक्शन की गणना करें,

$$
\operatorname{erfcx}(x)
= e^{x^2} \operatorname{erfc}(x)
\quad \text{के लिए} \quad x \in \mathbb{C} \, .
$$

यह बड़े $x$ के लिए $e^{x^2} \operatorname{erfc}(x)$ का सटीक संस्करण है। यह भी ध्यान दें कि $\operatorname{erfcx}(-ix)$ Faddeeva फ़ंक्शन `w(x)` की गणना करता है।

बाहरी लिंक: [DLMF 7.2.3](https://dlmf.nist.gov/7.2.3), [Wikipedia](https://en.wikipedia.org/wiki/Error_function#Complementary_error_function).

देखें: [`erfc(x)`](@ref erfc).

# द्वारा कार्यान्वयन

  * `Float32`/`Float64`: C मानक गणित पुस्तकालय   [libm](https://en.wikipedia.org/wiki/C_mathematical_functions#libm).
  * `BigFloat`: MPFR के पास इस फ़ंक्शन के लिए एक ओपन TODO आइटम है, तब तक, हम पूंछ के लिए   [DLMF 7.12.1](https://dlmf.nist.gov/7.12.1) का उपयोग करते हैं।
