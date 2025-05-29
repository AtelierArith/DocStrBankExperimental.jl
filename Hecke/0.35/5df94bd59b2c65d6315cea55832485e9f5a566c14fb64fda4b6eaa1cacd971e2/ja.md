```
conjugates_complex(x::AbsSimpleNumFieldElem, abs_tol::Int) -> Vector{AcbFieldElem}
```

複素数の共役を $x$ の要素として `AcbFieldElem` 型で計算します。複素数の共役 $\sigma_{r+1}(x),...,\sigma_{r+2s}(x)$ を次のように順序付けることを思い出してください：$\sigma_{i}(x) = \overline{\sigma_{i + s}(x)}$ であり、$r + 1 \leq i \leq r + s$ の範囲です。

返される配列の各エントリ $y$ は `radius(real(y)) < 2^-abs_tol` および `radius(imag(y)) < 2^-abs_tol` を満たします。 ```
