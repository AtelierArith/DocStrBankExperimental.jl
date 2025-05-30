```
ellipk(m)
```

पूर्ण अंडाकार समाकलन का 1st प्रकार $K(m)$ के लिए गणना करता है, जिसके लिए पैरामीटर $m$ दिया गया है

$$
\operatorname{ellipk}(m)
= K(m)
= \int_0^{ \frac{\pi}{2} } \frac{1}{\sqrt{1 - m \sin^2 \theta}} \, \mathrm{d}\theta
\quad \text{के लिए} \quad m \in \left( -\infty, 1 \right] \, .
$$

बाहरी लिंक: [DLMF 19.2.8](https://dlmf.nist.gov/19.2.8), [Wikipedia](https://en.wikipedia.org/wiki/Elliptic_integral#Notational_variants).

देखें: [`ellipe(m)`](@ref SpecialFunctions.ellipe).

# तर्क

  * `m`: पैरामीटर $m$, जो डोमेन $(-\infty,1]$ तक सीमित है, अंडाकार गुणांक $k$ से $k^2=m$ द्वारा संबंधित है और मापांक कोण $\alpha$ से $k = \sin \alpha$ द्वारा संबंधित है।

# कार्यान्वयन

[fukushima_2009](@citet) में दिए गए टुकड़ों के अनुसार अनुमानित बहुपद का उपयोग करना।

$$
m < 0
$$

के लिए, [fukushima_2015](@citet) द्वारा अनुसरण किया गया।

इस पत्र में सुझाए अनुसार, डोमेन $(-\infty,1]$ तक सीमित है।
