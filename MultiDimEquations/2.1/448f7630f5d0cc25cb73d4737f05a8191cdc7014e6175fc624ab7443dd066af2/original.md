```
MultiDimEquations
```

The package provides handy functions to work with NDSparse (from IndexedTables.jl package) or standard arrays in order to write equations in a concise and readable way. The formers can be accessed by name, but are somehow slower, the latters are faster but need to be accessed by position.

`defVars()` defines either empty NDSparse with the dimensions (axis) required or arrays with the required size and prefilled with `missing` values. More variables can be defined at once.

`defLoadVar()` and `defLoadVars()` allow to define and import the variables from a DataFrame in long format (dim1|dim2|...|value), with the second one allowing to import more varaibles at once, given the presence of a column in the database with the variable names.

`@meq` is a macro that allows to write your "model equations" more concisely, e.g. `@meq par1[d1 in DIM1, d2 in DIM2, dfix3] =  par2[d1,d2]+par3[d1,d2]` would be expanded to use the list comprehension expression above: `[par1[d1,d2,dfix3] =  par2[d1,d2]+par3[d1,d2] for d1 in DIM1, d2 in DIM2]`
