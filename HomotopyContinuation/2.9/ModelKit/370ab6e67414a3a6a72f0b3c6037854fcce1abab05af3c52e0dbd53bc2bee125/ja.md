```
@var variable1 variable2 ...
```

指定された名前で変数を宣言し、変数バインディングを自動的に作成します。このマクロは、`Array`の変数を作成するためのインデックス表記をサポートしています。

## 例

```julia-repl
julia> @var a b x[1:2] y[1:2,1:3]
(a, b, Variable[x₁, x₂], Variable[y₁₋₁ y₁₋₂ y₁₋₃; y₂₋₁ y₂₋₂ y₂₋₃])

julia> a
a

julia> b
b

julia> x
2-element Array{Variable,1}:
 x₁
 x₂

julia> y
2×3 Array{Variable,2}:
 y₁₋₁  y₁₋₂  y₁₋₃
 y₂₋₁  y₂₋₂  y₂₋₃
```
