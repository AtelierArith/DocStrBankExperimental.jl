```
merged_add!(A,B)
merged_add!(A,B, α=1.0)
merged_add!(A,B, α=1.0,β=1.0)
```

It updates `A` by `αA + βB` (i.e., performing `A = αA + βB`). The default (α,β) is (1.0,1.0), which results in `A + B`.
