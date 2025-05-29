```
@argumend [n_suggestions=3] [cutoff=0.6] funcdef
```

This macro lets you automatically suggest similarly-spelled keywords:

```julia
@argumend function f(a, b; niterations=10, kw2=2)
    a + b - niterations + kw2
end
```

This results in a nicer mechanism for MethodErrors:

```julia
julia> f(1, 2; iterations=1)
ERROR: SuggestiveMethodError: in call to `f`, found unsupported
       keyword argument: `iterations`, perhaps you meant `niterations`
```

This function computes closeness between the mistyped keyword argument by counting the maximum number of matching subsequences with all the other keyword arguments.

You can customize the number of suggestions by specifying it in the macro. You can also control the closeness threshold with `cutoff`.
