```
ellipe(m)
```

पूर्ण अंडाकार समाकल का 2nd प्रकार $E(m)$ के लिए गणना करता है, जिसके लिए पैरामीटर $m$ दिया गया है

$$
\operatorname{ellipe}(m)
= E(m)
= \int_0^{ \frac{\pi}{2} } \sqrt{1 - m \sin^2 \theta} \, \mathrm{d}\theta
\quad \text{के लिए} \quad m \in \left( -\infty, 1 \right] .
$$

बाहरी लिंक: [DLMF 19.2.8](https://dlmf.nist.gov/19.2.8), [Wikipedia](https://en.wikipedia.org/wiki/Elliptic_integral#Complete_elliptic_integral_of_the_second_kind).

इसी तरह: [`ellipk(m)`](@ref SpecialFunctions.ellipk).

# तर्क

  * `m`: पैरामीटर $m$, जो डोमेन $(-\infty,1]$ तक सीमित है, अंडाकार गुणांक $k$ से $k^2=m$ द्वारा संबंधित है और मापांक कोण $\alpha$ से $k=\sin \alpha$ द्वारा संबंधित है।

# कार्यान्वयन

[फुकुशिमा_2015](@citet) में दिए गए टुकड़ा-वार अनुमानित बहुपद का उपयोग करना

$$
म<0
$$

के लिए, [फुकुशिमा_2015](@citet) द्वारा अनुसरण किया गया।

इस पत्र में सुझाए अनुसार, डोमेन $(-\infty,1]$ तक सीमित है।
