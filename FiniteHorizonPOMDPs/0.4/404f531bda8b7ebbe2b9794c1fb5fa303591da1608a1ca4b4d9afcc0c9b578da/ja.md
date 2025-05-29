```
fixhorizon(m::Union{MDP,POMDP}, horizon::Int)
```

無限ホライズン (PO)MDP `m` と `horizon` を新しい構造にラップして有限ホライズン (PO)MDP を作成します。
