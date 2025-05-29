```
get_preconditioner(M::AbstractManifold, mho::ManifoldHessianObjective, p, X)
```

対称的で正定値の前処理器（コスト関数 `F` のヘッセ行列の逆の近似）を、接ベクトル `X` に適用した点 `p` での [`ManifoldHessianObjective`](@ref) `mho` で評価します。
