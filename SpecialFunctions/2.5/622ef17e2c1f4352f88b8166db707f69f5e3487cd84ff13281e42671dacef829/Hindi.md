```
loggamma(a,x)
```

यह अपर अधूरा गामा फ़ंक्शन [`gamma(a,x)`](@ref) का लॉग लौटाता है:

$$
\log \Gamma(a,x) = \log \int_x^\infty t^{a-1} e^{-t} \mathrm{d}t
$$

जो मनमाने वास्तविक या जटिल `a` और `x` का समर्थन करता है।

यदि `a` और/या `x` जटिल है, तो `exp(loggamma(a,x))` `gamma(a,x)` से मेल खाता है (फ्लोटिंग-पॉइंट त्रुटि के अपवाद के साथ), लेकिन `loggamma(a,x)` `log(gamma(a,x))` से $2\pi i$ के पूर्णांक गुणांक के द्वारा भिन्न हो सकता है (यानी यह एक अलग शाखा कट का उपयोग कर सकता है)।

देखें भी [`loggamma(x)`](@ref)।
