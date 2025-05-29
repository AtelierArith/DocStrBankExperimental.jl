```
evolve(f)
```

Create the DynamicIterator corresponding to the evolution

```
    x = f(x)
```

Integer keys default to increments. Integer control default to keys (and repetitions).

```
julia> collect(take(from(Evolve(x->x + 1), 10), 5))
5-element Array{Any,1}:
 10
 11
 12
 13
 14
```
