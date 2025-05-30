```julia
ScalarOperator(val; update_func, accepted_kwargs)

```

`Number` または `AbstractArray` サブタイプに適用できる線形スケーリング演算子を表します。その状態は、演算子評価中 (`L([v,] u, p, t)`) にユーザー提供の `update_func` によって更新されるか、`update_coefficients[!]` への呼び出しによって更新されます。どちらも再帰的に更新関数 `update_func` を呼び出し、次のシグネチャを持つと仮定されます。

```
update_func(oldval::Number, u, p, t; <accepted kwargs>) -> newval
```

`update_func` によって受け入れられるキーワード引数のセットは、`accepted_kwargs` というキーワード引数を介して `ScalarOperator` に `Symbol` のタプルとして提供されなければなりません。`accepted_kwargs` が提供されていない場合、`kwargs` を `update_func` に渡すことはできません。

!!! warning
    ユーザー提供の `update_func[!]` は、その計算に `u` を使用してはなりません。`update_func[!]` への位置引数 `(u, p, t)` は、`update_coefficients[!](L, u, p, t)` によって渡され、ここで `u` は複合 `AbstractSciMLOperator` への入力ベクトルです。そのため、`u` の値や形状は、`update_func[!]` が期待する入力に対応しない可能性があります。演算子の状態がその入力ベクトルに依存する場合、それは定義上非線形演算子です。このような非線形性は `FunctionOperator` に保持することをお勧めします。このトピックは（この問題）[https://github.com/SciML/SciMLOperators.jl/issues/159] でさらに議論されています。


# インターフェース

遅延スカラー代数は `AbstractSciMLScalarOperator` に対して定義されています。このインターフェースは、遅延加算、減算、乗算、および除算をサポートします。

# 例

```
v = zero(4)
u = rand(4)
p = nothing
t = 0.0

val_update = (a, u, p, t; scale = 0.0) -> copy(scale)
α = ScalarOperator(0.0; update_func = val_update; accepted_kwargs = (:scale,))
β = 2 * α + 3 / α

# Lをアウトオブプレースで更新し、評価
β(u, p, t; scale = 1.0)

# Lをインプレースで更新し、評価
β(v, u, p, t; scale = 1.0)
```
