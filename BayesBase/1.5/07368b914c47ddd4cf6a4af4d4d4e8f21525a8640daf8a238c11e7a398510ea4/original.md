```
promote_variate_type(::Type{D}, distribution_type) where { D <: Distribution }
```

Promotes (if possible) a `distribution_type` to be of the same variate form as `D`.
