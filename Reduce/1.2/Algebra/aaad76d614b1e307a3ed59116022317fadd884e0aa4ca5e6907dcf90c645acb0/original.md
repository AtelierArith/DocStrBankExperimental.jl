```
factor(r...)
```

This declaration takes a list of identifiers or kernels as argument. `factor` is not a factoring command (use `factorize` or the `factor` switch for this purpose); rather it is a separation command. All terms involving fixed powers of the declared expressions are printed as a product of the fixed powers and a sum of the rest of the terms.

For example, after the declaration

```Julia
julia> Algebra.factor(:x)
```

the polynomial $(x + y + 1)^2$ will be printed as

```
         2                  2  
        x  + 2*x*(y + 1) + y  + 2*y + 1
```

All expressions involving a given prefix operator may also be factored by putting the operator name in the list of factored identifiers. For example:

```Julia
julia> Algebra.factor(:x,:cos,:(sin(x))
```

causes all powers of `x` and `sin(x)` and all functions of `cos` to be factored.
