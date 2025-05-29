# Hadamard sense right rectangular approximating algorithm

```
fracdiff(f, α, a, x, h, HadamardTrap())
```

Using finite part integral of **right rectangular formula** to compute the fractional hadamard derivative.

### Example

```julia-repl
julia> fracdiff(x->x, 0.5, 0, 1, 0.001, HadamardRRect())
0.9738507879228337
```
