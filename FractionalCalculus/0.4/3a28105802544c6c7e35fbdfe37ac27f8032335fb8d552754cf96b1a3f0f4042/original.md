# Riemann Liouville sense integral using Triangular Strip Matrix to discrete.

```
fracint(f, α, end_point, h, RLIntMatrix())
```

Using Triangular Strip Matrix to approximate fractional integral.

### Example

```julia-repl
julia> fracint(x->x^5, 0.5, 2.5, 0.0001, RLIntMatrix())
```

!!! info
    Triangular Strip Matrix method returns the derivative in the interval $[0, T]$ in `Vector`


!!! tip
    With the advancing Triangular Strip Matrix method, you can not only compute fractional integrals, integer order, higher order integral is also supported!!


Try to set α as an integer, arbitrary integer of course! I promise you would enjoy it😏

Using [Triangular Strip Matrix](https://en.wikipedia.org/wiki/Triangle_strip) to discrete the integral.
