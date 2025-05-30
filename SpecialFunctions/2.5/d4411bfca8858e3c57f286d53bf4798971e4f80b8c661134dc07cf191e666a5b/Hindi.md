```
gamma(z)
```

जटिल $z$ के लिए गामा फ़ंक्शन की गणना करें, जिसे इस प्रकार परिभाषित किया गया है

$$
\Gamma(z)
:=
\begin{cases}
    n!
    & \text{के लिए} \quad z = n+1 \;, n = 0,1,2,\dots
    \\
    \int_0^\infty t^{z-1} e^{-t} \, \mathrm{d}t
    & \text{के लिए} \quad \Re(z) > 0
\end{cases}
$$

और पूरे जटिल क्षेत्र में विश्लेषणात्मक निरंतरता द्वारा।

# उदाहरण

```jldoctest
julia> gamma(0)
Inf

julia> gamma(1)
1.0

julia> gamma(2)
1.0

julia> gamma(0.5)^2 ≈ π
true

julia> gamma(4 + 1) == prod(1:4) == factorial(4)
true
```

बाहरी लिंक: [DLMF 5.2.1](https://dlmf.nist.gov/5.2.1), [Wikipedia](https://en.wikipedia.org/wiki/Gamma_function).

देखें: [`loggamma(z)`](@ref SpecialFunctions.loggamma) के लिए $\log \Gamma(z)$ और [`gamma(a,z)`](@ref SpecialFunctions.gamma(::Number,::Number)) के लिए अपर अधूरा गामा फ़ंक्शन $\Gamma(a,z)$।

# कार्यान्वयन द्वारा

  * `Float`: C मानक गणित पुस्तकालय   [libm](https://en.wikipedia.org/wiki/C_mathematical_functions#libm).
  * `Complex`: द्वारा `exp(loggamma(z))`.
  * `BigFloat`: बहु-सटीकता फ्लोटिंग-पॉइंट के लिए C पुस्तकालय [MPFR](https://www.mpfr.org/)
