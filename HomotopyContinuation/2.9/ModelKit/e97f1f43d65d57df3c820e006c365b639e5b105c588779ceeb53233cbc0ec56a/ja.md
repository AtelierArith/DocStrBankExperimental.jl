```
Homotopy(exprs, vars, t, parameters = Variable[])
```

与えられた [`Expression`](@ref)s `exprs` から、`vars` が指定された変数であり、`t` がシステムのファミリーをパラメータ化する専用の変数であるホモトピー `H(vars,t)` を作成します。`parameters` 引数は、特定の [`Variable`](@ref)s をパラメータとして宣言することを可能にします。

## 例

```julia-repl
julia> @var x y t;

julia> H = Homotopy([x + t, y + 2t], [y, x], t)
Homotopy in t of length 2
 2 variables: y, x

 t + x
 2*t + y

julia> H([2, 3], 0)
2-element Array{Int64,1}:
 3
 2


julia> H([2, 3], 1)
2-element Array{Int64,1}:
 4
 4
```

追加の変数を宣言することも可能です。

```julia-repl
julia> @var x y t a b;
julia> H = Homotopy([x^2 + t*a, y^2 + t*b], [x, y], t, [a, b])
Homotopy in t of length 2
 2 variables: x, y
 2 parameters: a, b

 a*t + x^2
 b*t + y^2
julia> H([2, 3], 1, [5, 2])
2-element Array{Int64,1}:
 9
 11
```
