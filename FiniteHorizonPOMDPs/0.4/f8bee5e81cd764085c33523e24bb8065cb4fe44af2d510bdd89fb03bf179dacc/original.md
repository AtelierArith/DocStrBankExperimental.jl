```
stage(m::Union{MDP,POMDP}, ss)::Int
stage(m::Union{MDP,POMDP}, o)::Int
stage(d)::Int
```

Considering a variable or distribution containing its stage assignment, return the number of its stage.
