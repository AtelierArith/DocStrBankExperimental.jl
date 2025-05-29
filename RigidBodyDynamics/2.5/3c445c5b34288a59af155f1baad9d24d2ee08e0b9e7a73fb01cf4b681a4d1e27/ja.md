```julia
momentum_matrix!(mat, state, transformfun)

```

与えられた状態における`Mechanism`の運動量行列$A(q)$を計算します。

運動量行列は、`Mechanism`の関節速度ベクトル$v$をその総運動量にマッピングします。

[`MomentumMatrix`](@ref)も参照してください。

`out`引数は、`Mechanism`の関節速度ベクトル$v$の次元と同じ数の列を持つ可変の`MomentumMatrix`でなければなりません。

`transformfun`は、各関節に関連付けられた個々の運動量行列ブロックを`out`が表現されているフレームに変換するために使用できる呼び出し可能な関数です。

このメソッドは、計算をインプレースで行い、動的メモリ割り当てを行いません。
