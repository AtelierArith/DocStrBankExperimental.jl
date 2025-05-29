```
ParametrizedCurve(fun, range = (0.0, 1.0))
```

パラメータ化された曲線は、与えられた `range` 内の（無次元の）パラメータ `t` を空間内の `Point` にマッピングする関数 `fun` によって定義される曲線です。

## 例

```julia
ParametrizedCurve(t -> Point(cos(t), sin(t)), (0, 2π))
```
