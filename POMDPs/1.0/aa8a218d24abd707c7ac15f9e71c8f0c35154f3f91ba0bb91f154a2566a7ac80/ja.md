```
actiontype(t::Type)
actiontype(p::Union{POMDP,MDP})
```

問題タイプの状態タイプを返します（`POMDP{S,A,O}`の`S`）。

```
type A <: POMDP{Bool, Int, Bool} end

actiontype(A) # returns Int
```
