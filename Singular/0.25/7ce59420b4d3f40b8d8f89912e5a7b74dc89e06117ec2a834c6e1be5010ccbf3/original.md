```
isequal(I1::sideal{S}, I2::sideal{S}) where S <: SPolyUnion
```

Return `true` if the given ideals have the same generators in the same order. Note that two algebraically equal ideals with different generators will return `false`.
