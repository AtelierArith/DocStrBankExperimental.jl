```
update!(
    μtuner::MuTunerLogger{T,S},
    n::Number, N²::Number, s::S=one(S)
) where {T<:AbstractFloat, S<:Number}
```

新しい粒子密度 `n`、総粒子数の二乗 `N²`、および符号 `s` の測定値に基づいて化学ポテンシャルを更新します。
