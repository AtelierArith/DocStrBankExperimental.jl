```
crystaldensity(lattice::Lattice, atoms)
crystaldensity(cell::Cell)
```

Calculate the density of a crystal structure.

Here, `atoms` is an iterable of atomic numbers, element names, symbols, or `Mendeleev.Element`s. You can extend the `atomicmass` method to work with custom types.
