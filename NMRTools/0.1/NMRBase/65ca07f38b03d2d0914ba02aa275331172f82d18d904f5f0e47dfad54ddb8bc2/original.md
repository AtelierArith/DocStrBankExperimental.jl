```
WindowFunction
```

Abstract type to represent apodization functions.

Window functions are represented by subtypes of the abstract type `WindowFunction`, each of which contain appropriate parameters to specify the particular function applied. In addition, the acquisition time `tmax` is also stored (calculated at the point the window function is applied, i.e. after linear prediction but before zero filling).
