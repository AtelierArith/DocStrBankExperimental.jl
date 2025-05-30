```
erfcinv(x)
```

एक वास्तविक $x$ के लिए विपरीत त्रुटि पूरक कार्य की गणना करें, अर्थात

$$
\operatorname{erfcinv}(x) = \operatorname{erfc}^{-1}(x)
\quad \text{के लिए} \quad x \in \mathbb{R} \, .
$$

बाहरी लिंक: [Wikipedia](https://en.wikipedia.org/wiki/Error_function#Inverse_functions).

देखें: [`erfc(x)`](@ref erfc).

# कार्यान्वयन

[Blair (1976)](@cite blair_1976) में तालिकाबद्ध अनुपातात्मक अनुमानकों का उपयोग करते हुए `BigFloat` के लिए न्यूटन पुनरावृत्तियों के साथ।
