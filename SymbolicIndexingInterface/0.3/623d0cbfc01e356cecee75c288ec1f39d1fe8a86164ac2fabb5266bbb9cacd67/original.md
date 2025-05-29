```
symbolic_container(indp)
```

Using `indp`, return an object that implements the index provider interface. In case `indp` itself implements the interface, `indp` can be returned as-is. All index provider interface methods fall back to calling the same method on `symbolic_container(indp)`, so this may be used for trivial implementations of the interface that forward all calls to another object.

Note that this method is optional. Thus the correct method to check for a fallback is:

```julia
hasmethod(symbolic_container, Tuple{typeof(indp)}) && symbolic_container(indp) != indp
```
