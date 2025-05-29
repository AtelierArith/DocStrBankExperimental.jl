```
mirror_symmetric_qubit_kets( θ :: Real ) :: Vector{Ket{Float64}}
```

x-z平面のブロッホ球におけるキュービットケットのトリプレットを返します。最初のケットは $|0\rangle$ で、他の2つはz軸に対して対称であり、$|\pm\rangle = \cos(\theta)|0 \rangle \pm \sin(\theta)|1\rangle$ です。

入力:

  * `θ ∈ [0,π/2]`: $|0\rangle$ と対称ケットの間のヒルベルト空間の角度。
