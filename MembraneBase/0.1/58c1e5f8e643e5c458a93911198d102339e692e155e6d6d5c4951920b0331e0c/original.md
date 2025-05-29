```
isotherm_dataset(x::Matrix, y::Matrix, component::Int)
```

converts two isotherm components into a vector steps in the format of [(type*x, type*y)...] For multicomponent isotherms, the format is dataset[step] = [[xcomp1, xcomp2, ...], [ycomp1, ycomp2, ...]]     e.g., `mydataset = Isotherm.dataset(myisotherm.partial_pressures, myisotherm.concentrations)` gives a vector of vectors in the format of:         myset[1] = [[(pressure of component 1), (pressure of component 2), ...], [(conc of component 1), (conc of component 2), ...]]
