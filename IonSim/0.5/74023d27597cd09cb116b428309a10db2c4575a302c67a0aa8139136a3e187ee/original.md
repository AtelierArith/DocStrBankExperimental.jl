```
create(v::VibrationalMode)
```

returns the creation operator for `v` such that: `create(v) * v[i] = √(i+1) * v[i+1]`.
