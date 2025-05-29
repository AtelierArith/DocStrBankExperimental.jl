`words_transversal(gens,p,action::Function=^)`

トランスバースの記録単語。`orbit(gens,p,action)`のキーを持つ`Dict` `t`を返し、ここで`t[x]`は整数のシーケンスであり、`x==action(p,prod(gens[t[x]]))`となります。つまり、`p`の軌道の各要素`x`は、`gens`の単語として記述され、`p`を`x`に持っていく要素です。

```julia-repl
julia> words_transversal([Perm(1,2),Perm(2,3)],1)
OrderedDict{Int64, Vector{Int64}} with 3 entries:
  1 => []
  2 => [1]
  3 => [1, 2]
```
