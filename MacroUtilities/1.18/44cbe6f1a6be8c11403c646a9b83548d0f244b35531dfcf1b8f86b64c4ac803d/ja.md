```
ReplaceSymbols(expr::Expr, to_replace::Set{Symbol})

ReplaceSymbols(expr::Expr, to_replace::Symbol...)
```

`replace_symbols`の関数形式、すなわち、`to_replace`にある`Symbol`の集合`x_old`が与えられた場合、

この型は`(x_old1 => x_new1, ..., x_oldk => x_newk) -> Expr`の形式の関数として機能し、`expr`内の各`x_oldj`のインスタンスは`x_newj`に再帰的に置き換えられます。

# 例

```julia-repl
julia> f = ReplaceSymbols(:(g(_)::T), :_);

julia> f(:_ => :x)
:(g(x)::T)
```
