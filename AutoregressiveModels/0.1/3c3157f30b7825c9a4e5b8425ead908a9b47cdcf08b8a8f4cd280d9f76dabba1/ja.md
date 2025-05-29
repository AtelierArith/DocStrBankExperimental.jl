```
impulse!(out, r::VectorAutoregression, ε0::AbstractVecOrMat; kwargs...)
impulse!(out, r::VectorAutoregression, ishock::Union{Integer, AbstractRange}; kwargs...)
```

`ε0` または `ishock` で指定されたショックに対するインパルス応答を計算し、結果を配列 `out` に格納します。計算されるホライズンの数は `out` の第二次元によって決まります。時間的（短期）制約に基づいて特定された構造的ショックに対する応答は、`r` に対してコレスキー分解が行われている場合に計算できます。詳細は [`impulse`](@ref) および [`simulate!`](@ref) を参照してください。

ベクトルとしての `ε0` は、各変数へのインパルスの大きさを指定します。行列の列は、複数のインパルスとして解釈され、結果は配列 `out` の第三次元に別々に格納されます。あるいは、`ishock` は影響を受ける単一の変数のインデックスを指定します。インデックスの範囲は複数のインパルスとして解釈されます。キーワード `choleskyshock` が `true` の場合、指定されたショックインデックスは、縮小形式のショックではなく構造的ショックを指すものとして解釈されます。

# キーワード

  * `nlag::Integer=arorder(var)`: シミュレーションに使用される `var` からのラグの数。
  * `choleskyshock::Bool=false`: いかなるショックインデックスが構造的ショックを指すかどうか。
