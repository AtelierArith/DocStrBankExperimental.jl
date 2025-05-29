```
statetype(t::Type)
statetype(p::Union{POMDP,MDP})
```

問題タイプの状態タイプを返します（`POMDP{S,A,O}`の`S`）。

```
type A <: POMDP{Int, Bool, Bool} end

statetype(A) # returns Int
```
