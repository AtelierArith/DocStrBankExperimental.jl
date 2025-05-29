```julia
momentum_matrix!(mat, state, root_to_desired)

```

与えられた状態における`Mechanism`の運動量行列$A(q)$を計算します。

運動量行列は、`Mechanism`の関節速度ベクトル$v$をその総運動量にマッピングします。

[`MomentumMatrix`](@ref)も参照してください。

`out`引数は、`Mechanism`の関節速度ベクトル$v$の次元と同じ数の列を持つ可変の`MomentumMatrix`でなければなりません。

`root_to_desired`は、`Mechanism`のルートフレームから`out`が表現されるフレームへの変換です。

このメソッドは、動的メモリ割り当てを行わずにインプレースで計算を行います。
