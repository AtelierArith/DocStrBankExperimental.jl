```
RewritingSystem{W<:AbstractWord, O<:Ordering}
RewritingSystem(rwrules::Vector{Pair{W,W}}, order[; confluent=false, reduced=false])
```

`RewritingSystem` は `W<:AbstractWord` の順序付けられた（`order` によって）書き換えルールのリストを保持します。
