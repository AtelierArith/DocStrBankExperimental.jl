```julia
update_coefficients!(L, u, p, t; kwargs...)

```

`L`の状態を`u`、入力ベクトル、`p`パラメータオブジェクト、`t`、およびキーワード引数に基づいてインプレースで更新します。内部的に、`update_coefficients!`は、位置引数`(u, p, t)`と、オペレーターに提供されたシンボルに対応するキーワード引数`accepted_kwargs`を使用して、`L`内のすべてのコンポーネントオペレーターに対してユーザー提供のミューテーション`update_func!`メソッドを呼び出します。

!!! warning
    ユーザー提供の`update_func[!]`は、その計算で`u`を使用してはいけません。`update_func[!]`への位置引数`(u, p, t)`は、`update_coefficients[!](L, u, p, t)`によって渡され、ここで`u`は合成`AbstractSciMLOperator`への入力ベクトルです。そのため、`u`の値や形状は、`update_func[!]`が期待する入力に対応しない場合があります。オペレーターの状態がその入力ベクトルに依存する場合、それは定義上、非線形オペレーターです。このような非線形性は`FunctionOperator.`に保持することをお勧めします。このトピックは（この問題）[https://github.com/SciML/SciMLOperators.jl/issues/159]でさらに議論されています。


# 例

```
using SciMLOperator

_A = rand(4, 4)
mat_update_func! = (L, u, p, t; scale = 1.0) -> copy!(A, _A)

M = MatrixOperator(zeros(4,4); update_func! = mat_update_func!)

L = M + IdentityOperator(4)

u = rand(4)
p = rand(4)
t = 1.0

update_coefficients!(L, u, p, t)
L * u
```
