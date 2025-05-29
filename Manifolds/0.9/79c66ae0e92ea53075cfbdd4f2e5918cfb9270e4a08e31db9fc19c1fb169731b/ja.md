```
rand(M::Grassmann; σ::Real=1.0, vector_at=nothing)
```

`vector_at`が`nothing`の場合、標準偏差`σ`を持つランダム（ガウス）行列を生成し、対応するサイズで直交正規な[`Grassmann`](@ref)多様体`M`上のランダム点`p`を返します。

`vector_at`が`nothing`でない場合、平均ゼロで標準偏差`σ`を持つ接空間$T_p\mathrm{Gr}(n,k)$からの（ガウス）ランダムベクトルを返し、`vector_at`での接空間にランダム行列を射影します。
