```julia
momentum_matrix!(out, state)

```

与えられた状態における`Mechanism`の運動量行列$A(q)$を計算します。

運動量行列は、`Mechanism`の関節速度ベクトル$v$をその総運動量にマッピングします。

[`MomentumMatrix`](@ref)も参照してください。

`out`引数は、`Mechanism`の関節速度ベクトル$v$の次元と同じ数の列を持つ可変の`MomentumMatrix`でなければなりません。

[`momentum_matrix!(out, state, root_to_desired)`](@ref)を参照してください。`state`を使用して、`Mechanism`のルートフレームから`out`が表現されているフレームへの変換を計算します。

このメソッドは、インプレースで計算を行い、動的メモリ割り当てを行いません。
