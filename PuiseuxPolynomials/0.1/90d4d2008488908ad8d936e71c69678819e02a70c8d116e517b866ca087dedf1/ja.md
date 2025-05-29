`degree(m::Mvp[,v::Symbol])`

モノミアルの `degree` は、変数の指数の合計です。`Mvp` の `degree` は、モノミアルの中で最も大きい次数です。

第二引数に変数名を指定すると、`degree` はその変数における多項式の次数を返します。

```julia-repl
julia> a=x^2+x*y
Mvp{Int64}: x²+xy

julia> degree(a), degree(a,:y), degree(a,:x)
(2, 1, 2)
```
