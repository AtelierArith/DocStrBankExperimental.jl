```
erfinv(x)
```

एक वास्तविक $x$ का उलटा त्रुटि फ़ंक्शन की गणना करें, अर्थात्

$$
\operatorname{erfinv}(x) = \operatorname{erf}^{-1}(x)
\quad \text{के लिए} \quad x \in \mathbb{R} \, .
$$

बाहरी लिंक: [Wikipedia](https://en.wikipedia.org/wiki/Error_function#Inverse_functions).

देखें: [`erf(x)`](@ref erf).

# कार्यान्वयन

[Blair (1976)](@cite blair_1976) में तालिकाबद्ध किए गए अनुपातात्मक अनुमानकों का उपयोग करते हुए `BigFloat` के लिए न्यूटन पुनरावृत्तियों के साथ।
