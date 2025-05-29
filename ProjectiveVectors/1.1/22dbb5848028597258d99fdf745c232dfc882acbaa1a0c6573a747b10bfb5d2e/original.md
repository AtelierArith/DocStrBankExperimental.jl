```
data(z::AbstractProjectiveVector)
```

Access the underlying vector of `z`. This is useful to pass the vector into some function which does not know the projective structure.

```
data(z::AbstractVector)
```

For general `AbstractVector`s this is just the identity.
