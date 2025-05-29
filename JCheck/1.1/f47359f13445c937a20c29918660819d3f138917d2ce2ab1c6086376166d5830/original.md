```
shrinkable(x)
```

Determines if `x` is shrinkable.

# Note

Shrinkage can easily be disabled for type `T` using overloading:

```
shrinkable(::T) = false
```
