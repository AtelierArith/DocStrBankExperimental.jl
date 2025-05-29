```
make_grid(sites::AtomList; atol=...)
```

Create a [`MaskedGrid`](@ref) from the sites. It is required by lattice preparation of Rydberg array. Because the grid will sort the sites by rows, we need `atol` (default value is 10 time sit data precision) determines up to what level of round off error, two atoms belong to the same row.
