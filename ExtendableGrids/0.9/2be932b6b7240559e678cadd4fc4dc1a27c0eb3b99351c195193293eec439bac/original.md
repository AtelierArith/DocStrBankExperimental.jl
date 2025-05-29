```
simplexgrid(X,Y; bregions=[1,2,3,4],cellregion=1)
```

Constructor for 2D grid from coordinate arrays. 

Boundary region numbers count counterclockwise:

| location | number |
| --------:| ------:|
|    south |      1 |
|     east |      2 |
|    north |      3 |
|     west |      4 |

The keyword arguments allow to overwrite the default region numbers.
