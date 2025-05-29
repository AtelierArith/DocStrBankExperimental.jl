# Extended help

```
concretize(X::LazySet)
```

### Algorithm

The default implementation returns `X`. All relevant lazy set types should override this behavior, typically by recursively calling `concretize` on the set arguments.
