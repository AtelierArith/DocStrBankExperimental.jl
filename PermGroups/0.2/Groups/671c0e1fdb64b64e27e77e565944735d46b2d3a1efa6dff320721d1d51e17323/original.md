`words_transversal(gens,p,action::Function=^)`

A   transversal   recording   words.   returns   a  `Dict`  `t`  with  keys `orbit(gens,p,action)` and where `t[x]` is a sequence of integers such that `x==action(p,prod(gens[t[x]]))`,  that is for each element `x` of the orbit of `p` describes as a word in `gens` an element bringing `p` to `x`.

```julia-repl
julia> words_transversal([Perm(1,2),Perm(2,3)],1)
OrderedDict{Int64, Vector{Int64}} with 3 entries:
  1 => []
  2 => [1]
  3 => [1, 2]
```
