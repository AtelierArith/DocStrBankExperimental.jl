```
SymbolicSimplex{L<:Union{Symbol,Char}} <: AbstractSimplex

SymbolicSimplex(label, w::AbstractVector{<:Integer})
SymbolicSimplex(label, n::Integer)
```

この型は、ラベルと頂点を列挙する非負整数の弱増加列によって与えられる「記号的単体」を表します。このような単体は、任意の整数が繰り返される場合に退化します。

ラベルは `Symbol` または `Char` 型であることができます。頂点番号は `0` から `31` の間でなければならず、次元は `24` を超えてはいけません。コンストラクタに整数 `n` が第二引数として渡されると、頂点は `0:n` になります。
