```
J = node(f, mach::Machine, args...)
```

動的な操作 `f`（`predict`、`predict_mean`、`transform` など）、ノードマシン `mach`、および引数 `args` をラップする動的な `Node` オブジェクト `J` を定義します。呼び出しの挙動は、`mach` のトレーニングの結果（および暗黙的にその引数に影響を与えるトレーニング結果）に依存します。

```
J() = f(mach, args[1](), args[2](), ..., args[n]())
J(rows=r) = f(mach, args[1](rows=r), args[2](rows=r), ..., args[n](rows=r))
J(X) = f(mach, args[1](X), args[2](X), ..., args[n](X))
```

一般的にこの後者の場合、`n=1` または `n=2` です。

```
predict(mach, X::AbsractNode, y::AbstractNode)
predict_mean(mach, X::AbstractNode, y::AbstractNode)
predict_median(mach, X::AbstractNode, y::AbstractNode)
predict_mode(mach, X::AbstractNode, y::AbstractNode)
transform(mach, X::AbstractNode)
inverse_transform(mach, X::AbstractNode)
```

`J = node(predict, mach, X, y)` などのショートカットです。

ノードを呼び出すことは再帰的な操作であり、ソースノード（またはノード）への呼び出しで終了します。*新しい* データ `X` に対してノードを呼び出すことは、そのようなノードの数が1つでない限り失敗します。

参照: [`Node`](@ref)、[`@node`](@ref)、[`source`](@ref)、[`origins`](@ref)。
