```
System(exprs::AbstractVector{Expression};
            variables = variables(exprssion),
            parameters = Variable[])
```

与えられた [`Expression`](@ref)s `exprs` からシステムを作成します。`variables` は変数の順序も決定します。`parameters` 引数は特定の [`Variable`](@ref)s をパラメータとして宣言することを可能にします。

```
System(support::AbstractVector{<:AbstractMatrix{<:Integer}},
       coefficients::AbstractVector{<:AbstractVector};
       variables,
       parameters = Variable[])
```

与えられたサポートと係数からシステムを作成します。

## 例

```julia-repl
julia> @var x y;
julia> F = System([x^2, y^2]; variables = [y, x])
System of length 2
 2 variables: y, x

 x^2
 y^2

# システムは呼び出し可能です。
# これは F を y=2 および x=3 で評価します
julia> F([2, 3])
2-element Array{Int64,1}:
 9
 4
```

パラメータを宣言することも可能です。

```julia-repl
julia> @var x y a b;
julia> F = System([x^2 + a, y^2 + b]; variables = [y, x], parameters = [a, b])
System of length 2
 2 variables: y, x
 2 parameters: a, b

 a + x^2
 b + y^2

julia> F([2, 3], [5, -2])
 2-element Array{Int64,1}:
  14
   2
```
