`AbsWord`は、いくつかの生成元に基づく自由群の要素を表します。生成元は`Symbols`によってインデックス付けされています。例えば、`a³b⁻²a`を表す`AbsWord`は、内部的には`[:a => 3, :b => -2, :a => 1]`として表されます。乗法は群の規則に従います：

```julia-repl
julia> w=AbsWord([:a => 3, :b => -2, :a => 1])
a³b⁻²a

julia> w*AbsWord([:a=>-1,:b=>1])
a³b⁻¹

```

正の`AbsWord`は、引数として`Symbols`を与えることで得られます。

```julia-repl
julia> AbsWord(:b,:a,:a,:b)
ba²b
```
