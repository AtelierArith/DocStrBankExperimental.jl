```
impulse!(out, var::VARProcess, ε0::AbstractVecOrMat; kwargs...)
impulse!(out, var::VARProcess, ishock::Union{Integer, AbstractRange}; kwargs...)
```

`var`プロセスに対するインパルスを`ε0`または`ishock`で指定し、その結果を配列`out`に格納します。計算されるホライズンの数は`out`の第二次元によって決まります。詳細は[`impulse`](@ref)および[`simulate!`](@ref)を参照してください。

ベクトルとして、`ε0`は各変数へのインパルスの大きさを指定します。行列の列は、結果が配列`out`の第三次元に別々に格納される複数のインパルスとして解釈されます。あるいは、`ishock`は影響を受ける単一の変数のインデックスを指定します。インデックスの範囲は複数のインパルスとして処理されます。

# キーワード

  * `nlag::Integer=arorder(var)`: シミュレーションに使用される`var`からのラグの数。
