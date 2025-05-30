```
erfi(x)
```

$ x $ के लिए परिभाषित काल्पनिक त्रुटि फ़ंक्शन की गणना करें,

$$
\operatorname{erfi}(x)
= -i \operatorname{erf}(ix)
\quad \text{के लिए} \quad x \in \mathbb{C} \, .
$$

बाहरी लिंक: [Wikipedia](https://en.wikipedia.org/wiki/Error_function#Imaginary_error_function).

देखें: [`erf(x)`](@ref erf).

# द्वारा कार्यान्वयन

  * `Float32`/`Float64`: C मानक गणित पुस्तकालय   [libm](https://en.wikipedia.org/wiki/C_mathematical_functions#libm).
