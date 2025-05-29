```
cor(d::StateSpaceSet) → m::SMatrix
```

Compute the corrlation matrix `m` from the columns of `d`, where `m[i, j]` is the correlation between `d[:, i]` and `d[:, j]`.
