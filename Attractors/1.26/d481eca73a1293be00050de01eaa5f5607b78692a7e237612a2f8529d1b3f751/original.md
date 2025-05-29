```
reset_mapper!(mapper::AttractorsMapper)
```

Reset all accumulated information of `mapper` so that it is as if it has just been initialized. Useful in `for` loops that loop over a parameter of the dynamical system stored in `mapper`.
