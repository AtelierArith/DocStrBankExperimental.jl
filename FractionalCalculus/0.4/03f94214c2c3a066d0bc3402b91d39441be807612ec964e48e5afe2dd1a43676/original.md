# Riemann Liouville sense fractional integral using fractional Simpson's formula to approximate.

### Example

```julia-repl
julia> fracint(x->x, 0.5, 1, 0.000001, RLIntSimpson())
0.7516516520541335
```

```tex
@inproceedings{Li2015NumericalMF,
  title={Numerical Methods for Fractional Calculus},
  author={Changpin Li and Fanhai Zeng},
  year={2015}
}
```

Using fractional Simpson's formula to discrete fractional integral.
