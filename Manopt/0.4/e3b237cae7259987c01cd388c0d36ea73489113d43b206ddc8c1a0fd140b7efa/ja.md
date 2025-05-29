```
get_preconditioner(M::AbstractManifold, mho::ManifoldHessianObjective, p, X)
```

コスト関数 `F` のヘッセ行列の逆の近似である対称正定値前処理器を、接ベクトル `X` に適用した点 `p` での [`ManifoldHessianObjective`](@ref) `mho` で評価します。
