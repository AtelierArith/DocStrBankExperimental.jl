```
@init begin
    pv₁ = init₁
    ...
    pvₙ = initₙ
end
```

Initialize private variables `pvᵢ` with initializer expression `initᵢ` for each task. This can be used for mutating objects in a data race-free manner.
