```
angle_between_vectors(
    v1::AbstractVector{T1}, v2::AbstractVector{T2}
) where {T1<:Number,T2<:Number}
```

2つのベクトル間の角度を、ドット積よりも数値的に安定した方法で計算します。

# 引数

-`v1::AbstractVector{<:Number}`: 計算のための最初のベクトル -`v2::AbstractVector{<:Number}`: 計算のための2番目のベクトル

# 戻り値

-`angle::Number`: 2つのベクトル間の角度
