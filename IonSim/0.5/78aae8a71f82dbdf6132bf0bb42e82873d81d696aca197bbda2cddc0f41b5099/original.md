```
destroy(v::VibrationalMode)
```

Returns the destruction operator for `v` such that: `destroy(v) * v[i] = √i * v[i-1]`.
