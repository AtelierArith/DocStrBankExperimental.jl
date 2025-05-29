```
simulate!(rng::AbstractRNG, m::MixedModel{T}; β=fixef(m), σ=m.σ, θ=T[])
simulate!(m::MixedModel; β=fixef(m), σ=m.σ, θ=m.θ)
```

モデル `m` からのシミュレーション応答ベクトルで応答 (すなわち `m.trms[end]`) を上書きします。

このシミュレーションには、ランダム効果の新しい値をサンプリングすることが含まれます。

`β` は、ピボットされたフルランクの係数ベクトル（cf. [`fixef`](@ref)）または、冗長な列に対応するエントリが無視されるフル次元の係数ベクトル（cf. [`coef`](@ref)）として指定できます。

!!! note
    `y::AbstractVector` を最初の引数（RNGを除く）として持つ `simulate!` メソッドと `simulate` メソッドは、シミュレーションされた応答を返します。これは、最初の引数として `m::MixedModel` を持つ `simulate!` メソッドがモデルの応答を修正し、修正されたモデル全体を返すのとは対照的です。

