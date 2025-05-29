# Hadamard sense left rectangular approximating algorithm

```
fracdiff(f, α, a, x, h, HadamardLRect())
```

Using finite part integral of **left rectangular formula** to compute the fractional hadamard derivative.

### Example

```julia-repl
julia> fracdiff(x->x, 0.5, 0, 1, 0.001, HadamardLRect())
0.9738507879228357
```
