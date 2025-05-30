```
logerfcx(x)
```

$$
x
$$

के स्केल किए गए पूरक त्रुटि फ़ंक्शन का प्राकृतिक लघुगणक निकालें, अर्थात

$$
\operatorname{logerfcx}(x) = \ln(\operatorname{erfcx}(x))
\quad \text{के लिए} \quad x \in \mathbb{R} \, .
$$

यह बड़े और नकारात्मक $x$ के लिए $\ln(\operatorname{erfcx}(x))$ का सटीक संस्करण है।

बाहरी लिंक: [Wikipedia](https://en.wikipedia.org/wiki/Error_function).

देखें: [`erfcx(x)`](@ref erfcx).

# कार्यान्वयन

[`erfc(x)`](@ref erfc) और [`erfcx(x)`](@ref erfcx) फ़ंक्शनों पर आधारित।
