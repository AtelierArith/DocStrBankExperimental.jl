```
stage(m::Union{MDP,POMDP}, ss)::Int
stage(m::Union{MDP,POMDP}, o)::Int
stage(d)::Int
```

変数またはそのステージ割り当てを含む分布を考慮して、そのステージの数を返します。
