```
obstype(t::Type)
```

問題タイプの状態タイプを返します（`POMDP{S,A,O}`の`S`）。

```
type A <: POMDP{Bool, Bool, Int} end

obstype(A) # returns Int
```
