```
detectvlinearity!(p::VRep, solver=default_solver(p); kws...)
```

V表現に含まれるすべての直線を検出し、冗長な直線をすべて削除します。

残りのキーワード引数 `kws` は [`detectvlinearity`](@ref) に渡されます。

## 例

表現

```julia
v = conichull([1, 1], [-1, -1])
```

には直線 `Line([1, 1])` が含まれています。
