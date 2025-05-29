```
Fresnel_S_erf(x)
```

The Fresnel function S(z) using the definition [wiki](https://en.wikipedia.org/wiki/Fresnel_integral) and the error function.

$$
    S(z) = \sqrt{\frac{\pi}{2}}\frac{1+i}{4} \bigg( \text{erf}\big(\frac{1+i}{\sqrt{2}}z \big) - i \text{erf}\big(\frac{1-i}{\sqrt{2}}z \big)\bigg)
$$

Returns the value $S(x)$
