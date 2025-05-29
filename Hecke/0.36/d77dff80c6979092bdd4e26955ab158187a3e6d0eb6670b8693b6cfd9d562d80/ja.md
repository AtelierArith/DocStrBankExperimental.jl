```
conjugates(x::AbsSimpleNumFieldElem, C::AcbField) -> Vector{AcbFieldElem}
```

$$
x
$$

の共役を`AcbFieldElem`型の要素として計算します。複素共役$\sigma_{r+1}(x),...,\sigma_{r+2s}(x)$は、$\sigma_{i}(x) = \overline{\sigma_{i + s}(x)}$となるように順序付けられます（$r + 1 \leq i \leq r + s$）。

`p`を`C`の精度とすると、返されるベクトルの各エントリ$y$はそれぞれ`radius(real(y)) < 2^-p`および`radius(imag(y)) < 2^-p`を満たします。 ```
