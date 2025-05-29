```
Fresnel_C_erf(x)
```

フレネル関数 C(z) は、定義 [wiki](https://en.wikipedia.org/wiki/Fresnel_integral) と誤差関数を使用しています。

$$
    C(z) = \sqrt{\frac{\pi}{2}}\frac{1-i}{4} \bigg( \text{erf}\big(\frac{1+i}{\sqrt{2}}z \big) + i \text{erf}\big(\frac{1-i}{\sqrt{2}}z \big)\bigg)
$$

値 $C(x)$ を返します。
