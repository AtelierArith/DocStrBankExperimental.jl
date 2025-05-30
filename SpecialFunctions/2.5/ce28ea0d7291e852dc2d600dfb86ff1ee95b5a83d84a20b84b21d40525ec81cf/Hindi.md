```
cosint(x)
```

$$
x
$$

के लिए परिभाषित कोसाइन इंटीग्रल फ़ंक्शन की गणना करें,

$$
\operatorname{Ci}(x)
:= \gamma + \log x + \int_0^x \frac{\cos (t) - 1}{t} \, \mathrm{d}t
\quad \text{के लिए} \quad
x > 0 \,,
$$

जहाँ $\gamma$ यूलेर-मास्केरोनी स्थिरांक है।

बाहरी लिंक: [DLMF 6.2.13](https://dlmf.nist.gov/6.2.13), [Wikipedia](https://en.wikipedia.org/wiki/Trigonometric_integral#Cosine_integral).

देखें: [`sinint(x)`](@ref SpecialFunctions.sinint).

# कार्यान्वयन

[MacLeod (1996)](@cite macleod_1996) में तालिका में दिए गए रैशनल अप्रॉक्सिमेंट्स का उपयोग करना।

नोट: $\text{Ci}(x)$ का दूसरा शून्य एक टाइपो है जिसे ठीक किया गया है: लेख में $r_1 = 3.38418 0422\mathbf{8} 51186 42639 78511 46402$ है, लेकिन वास्तव में: $r_1 = 3.38418 0422\mathbf{5} 51186 42639 78511 46402$ है।
