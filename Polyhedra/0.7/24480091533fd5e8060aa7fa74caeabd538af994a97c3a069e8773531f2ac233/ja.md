```
detecthlinearity!(p::HRep; kws...)
```

H-表現に含まれるすべての超平面を検出し、冗長な超平面をすべて削除します。

残りのキーワード引数 `kws` は [`detecthlinearity`](@ref) に渡されます。

## 例

表現

```julia
h = HalfSpace([1, 1], 1]) ∩ HalfSpace([-1, -1], -1)
```

は超平面 `HyperPlane([1, 1], 1)` を含みます。 ```
