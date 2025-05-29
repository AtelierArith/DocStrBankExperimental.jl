```
simplexgrid(X,Y,Z; bregions=[1,2,3,4,5,6],cellregion=1)
```

Constructor for 3D grid from coordinate arrays.  Boundary region numbers:

| location | number |
| --------:| ------:|
|    south |      1 |
|     east |      2 |
|    north |      3 |
|     west |      4 |
|   bottom |      5 |
|      top |      6 |

The keyword arguments allow to overwrite the default region numbers.
