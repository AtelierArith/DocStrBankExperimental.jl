```
gamma(a,x)
```

ऊपरी अधूरा गामा फ़ंक्शन लौटाता है

$$
\Gamma(a,x) = \int_x^\infty t^{a-1} e^{-t} \mathrm{d}t
$$

मनमाने वास्तविक या जटिल `a` और `x` का समर्थन करता है।

(साधारण गामा फ़ंक्शन [`gamma(x)`](@ref) $\Gamma(a) = \Gamma(a,0)$ के बराबर है। ऊपरी और निचले ($\gamma(a,x)$) अधूरे गामा फ़ंक्शंस को $\Gamma(a)$ द्वारा स्केल करने के लिए [`gamma_inc`](@ref) फ़ंक्शन को भी देखें।

बाहरी लिंक: [DLMF 8.2.2](https://dlmf.nist.gov/8.2.2), [Wikipedia](https://en.wikipedia.org/wiki/Incomplete_gamma_function)
