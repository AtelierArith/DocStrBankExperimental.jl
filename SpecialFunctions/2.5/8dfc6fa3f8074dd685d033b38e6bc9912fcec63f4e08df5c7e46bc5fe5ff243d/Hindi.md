```
gamma_inc_taylor_x(a,x,ind)
```

$$
P(a,x)
$$

की गणना करता है जो $P(a,x)/x^a$ के टेलर विस्तार पर आधारित है जिसे दिया गया है:

$$
J = -a * \sum_{1}^{\infty} (-x)^{n}/((a+n)n!)
$$

और $P(a,x)/x^a$ दिया गया है:

$$
(1 - J) / \Gamma(a+1)
$$

जो `gamma_inc(a,x,ind)` के पद-दर-पद समाकलन से प्राप्त होता है। इसका उपयोग तब किया जाता है जब `a < 1` और `x < 1.1` - [DiDonato & Morris (1986)](@cite didonato_1986) में समीकरण (9) देखें।

और देखें: [`gamma_inc(a,x,ind)`](@ref SpecialFunctions.gamma_inc)
