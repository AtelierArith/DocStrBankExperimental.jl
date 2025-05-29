```
ModulatedField(g::GeneratedField,modfcn::Abstract1DProfile)
```

Create a time-modulated form of a generated spatial field, useful for introducing a forcing field onto the grid. The supplied field `g` is modulated by a function `modfcn` with a specified profle shape. The resulting object can be evaluated with a single argument (time) and returns a `GridData` type object of the same type contained in `g`.
