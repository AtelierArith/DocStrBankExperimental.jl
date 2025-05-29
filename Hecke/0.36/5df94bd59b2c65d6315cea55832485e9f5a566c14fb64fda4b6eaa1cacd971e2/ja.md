```
conjugates_complex(x::AbsSimpleNumFieldElem, abs_tol::Int) -> Vector{AcbFieldElem}
```

複素数の共役を $x$ の型 `AcbFieldElem` の要素として計算します。複素数の共役は $\sigma_{r+1}(x),...,\sigma_{r+2s}(x)$ の順に並べられ、$\sigma_{i}(x) = \overline{\sigma_{i + s}(x)}$ となるようにします。ただし、$r + 1 \leq i \leq r + s$ です。

返される配列の各要素 $y$ は `radius(real(y)) < 2^-abs_tol` かつ `radius(imag(y)) < 2^-abs_tol` を満たします。
