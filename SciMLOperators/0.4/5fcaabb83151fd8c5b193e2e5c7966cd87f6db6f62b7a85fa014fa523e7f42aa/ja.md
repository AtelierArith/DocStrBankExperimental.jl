```julia
update_coefficients(L, u, p, t; kwargs...)

```

`L`の状態を`u`、入力ベクトル、`p`パラメータオブジェクト、`t`、およびキーワード引数に基づいて更新します。内部的に、`update_coefficients`は、位置引数`(u, p, t)`と、オペレーターにkwarg `accepted_kwargs`を介して提供されたシンボルに対応するキーワード引数を使用して、`L`のすべてのコンポーネントオペレーターに対してユーザー提供の`update_func`メソッドを呼び出します。

このメソッドは、非破壊的であり、完全に非変異的であり、`Zygote`互換です。

!!! warning
    ユーザー提供の`update_func[!]`は、その計算に`u`を使用してはなりません。位置引数`(u, p, t)`は、`update_coefficients[!](L, u, p, t)`によって`update_func[!]`に渡されます。ここで、`u`は合成`AbstractSciMLOperator`への入力ベクトルです。そのため、`u`の値や形状は、`update_func[!]`が期待する入力に対応しない場合があります。オペレーターの状態がその入力ベクトルに依存する場合、それは定義上、非線形オペレーターです。このような非線形性は`FunctionOperator.`に保持することをお勧めします。このトピックは（この問題）[https://github.com/SciML/SciMLOperators.jl/issues/159]でさらに議論されています。


# 例

```
using SciMLOperator

mat_update_func = (A, u, p, t; scale = 1.0) -> p * p' * scale * t

M = MatrixOperator(zeros(4,4); update_func = mat_update_func,
                   accepted_kwargs = (:state,))

L = M + IdentityOperator(4)

u = rand(4)
p = rand(4)
t = 1.0

L = update_coefficients(L, u, p, t; scale = 2.0)
L * u
```
