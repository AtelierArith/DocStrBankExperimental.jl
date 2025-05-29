```
conjugates(x::AbsSimpleNumFieldElem, abs_tol::Int) -> Vector{AcbFieldElem}
```

$$
x
$$

の共役を`AcbFieldElem`型の要素として計算します。複素共役を$\sigma_{r+1}(x),...,\sigma_{r+2s}(x)$の順に並べることを思い出してください。ここで、$\sigma_{i}(x) = \overline{\sigma_{i + s}(x)}$は$r + 1 \leq i \leq r + s$の範囲で成り立ちます。

返されるベクトルの各エントリ$y$は、それぞれ`radius(real(y)) < 2^-abs_tol`および`radius(imag(y)) < 2^-abs_tol`を満たします。
