```
Variable(name::Union{String,Symbol}, indices...) <: Number
```

変数を表すデータ構造。

```julia-repl
julia> Variable(:a)
a

julia> Variable(:x, 1)
x₁

julia> Variable(:x, 10, 5)
x₁₀₋₅
```

### 等価性と順序

変数はその `name` と `indices` によって識別されます。つまり、2つの変数は同じ `name` と `indices` を持つ場合に限り等しいです。

```julia-repl
julia> Variable(:a) == Variable(:a)
true

julia> Variable(:a, 1) == Variable(:a, 2)
false
```

同様に、変数はまず名前で辞書式に順序付けられ、その後にインデックスで順序付けられます。

```julia-repl
julia> Variable(:a, 1) < Variable(:a, 2)
true

julia> Variable(:a, 1) < Variable(:b, 1)
true

julia> a = [Variable(:a, i, j) for i in 1:2, j in 1:2]
2×2 Array{Variable,2}:
 a₁₋₁  a₁₋₂
 a₂₋₁  a₂₋₂

julia> sort(vec(a))
4-element Array{Variable,1}:
 a₁₋₁
 a₂₋₁
 a₁₋₂
 a₂₋₂
```
