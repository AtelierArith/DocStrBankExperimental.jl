# Hadamard sense trapezoidal approximating algorithm

```
fracdiff(f, α, a, x, h, HadamardTrap())
```

Using finite part integral of **trapezoidal formula** to compute the fractional hadamard derivative.

### Example

```julia-repl
julia> fracdiff(x->x, 0.5, 0, 1, 0.001, HadamardTrap())
0.9738507879228328
```
