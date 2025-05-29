```
rand(M::Grassmann; σ::Real=1.0, vector_at=nothing)
```

`vector_at`が`nothing`の場合、標準偏差`σ`で同じサイズのランダム（ガウス）行列を生成することによって、[`Grassmann`](@ref)多様体`M`上のランダム点`p`を返します。この行列は直交正規です。

`vector_at`が`nothing`でない場合、平均がゼロで標準偏差`σ`の（ガウス）ランダムベクトルを接空間$T_p\mathrm{Gr}(n,k)$から返します。これは、`vector_at`での接空間にランダム行列を射影することによって行われます。
