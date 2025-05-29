線形演算子を `AbstractMatrix` によって表現し、`AbstractVecOrMat` に適用できるようにします。その状態は、演算子評価中にユーザー提供の `update_func` によって更新されます（`L([v,], u, p, t)`）、または `update_coefficients[!](L, u, p, t)` の呼び出しによって更新されます。両者は再帰的に `update_function`、すなわち `update_func` を呼び出します。この関数は次のシグネチャを持つと仮定されます。

```
update_func(A::AbstractMatrix, u, p, t; <accepted kwargs>) -> newA
```

または

```
update_func!(A::AbstractMatrix, u ,p , t; <accepted kwargs>) -> [modifies A]
```

`update_func[!]` が受け入れるキーワード引数のセットは、`MatrixOperator` に `accepted_kwargs` というキーワード引数を介して `Symbol` のタプルとして提供されなければなりません。`accepted_kwargs` が提供されていない場合、`kwargs` を `update_func[!]` に渡すことはできません。

!!! 警告     ユーザー提供の `update_func[!]` は、その計算に `u` を使用してはなりません。`update_func[!]` への位置引数 `(u, p, t)` は、`update_coefficients[!](L, u, p, t)` によって渡されます。ここで `u` は、合成 `AbstractSciMLOperator` への入力ベクトルです。そのため、`u` の値や形状は、`update_func[!]` が期待する入力と一致しない可能性があります。演算子の状態がその入力ベクトルに依存する場合、それは定義上非線形演算子です。このような非線形性は `FunctionOperator` に保持することをお勧めします。このトピックは（この問題）[https://github.com/SciML/SciMLOperators.jl/issues/159] でさらに議論されています。

# インターフェース

遅延行列代数は `AbstractSciMLOperator` に対して定義されています。このインターフェースは、遅延加算、減算、乗算、逆行列、随伴、転置をサポートします。

# 例

アウトオブプレースの更新と使用

```
u = rand(4)
p = rand(4, 4)
t = rand()

mat_update = (A, u, p, t; scale = 0.0) -> t * p
M = MatrixOperator(0.0; update_func = mat_update; accepted_kwargs = (:scale,))

L = M * M + 3I
L = cache_operator(M, u)

# Lを更新して評価
v = L(u, p, t; scale = 1.0)
```

インプレースの更新と使用

```
v = zero(4)
u = rand(4)
p = nothing
t = rand()

mat_update! = (A, u, p, t; scale = 0.0) -> (copy!(A, p); lmul!(t, A))
M = MatrixOperator(zeros(4, 4); update_func! = val_update!; accepted_kwargs = (:scale,))
L = M * M + 3I

# Lをインプレースで更新して評価
L(v, u, p, t; scale = 1.0)
```
