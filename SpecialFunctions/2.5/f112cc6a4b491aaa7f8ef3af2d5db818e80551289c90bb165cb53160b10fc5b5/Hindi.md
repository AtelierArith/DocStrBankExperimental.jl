```
dawson(x)
```

$$
x
$$

का डॉसन फ़ंक्शन (स्केल्ड इमेजिनरी एरर फ़ंक्शन) की गणना करें, जिसे इस प्रकार परिभाषित किया गया है

$$
\operatorname{dawson}(x)
= \frac{\sqrt{\pi}}{2} e^{-x^2} \operatorname{erfi}(x)
\quad \text{के लिए} \quad x \in \mathbb{C} \, .
$$

यह बड़े $x$ के लिए $\frac{\sqrt{\pi}}{2} e^{-x^2} \operatorname{erfi}(x)$ का सटीक संस्करण है।

बाहरी लिंक: [DLMF 7.2.5](https://dlmf.nist.gov/7.2.5), [Wikipedia](https://en.wikipedia.org/wiki/Dawson_function).

देखें: [`erfi(x)`](@ref erfi).

# द्वारा कार्यान्वयन

  * `Float32`/`Float64`: C मानक गणित पुस्तकालय   [libm](https://en.wikipedia.org/wiki/C_mathematical_functions#libm).
