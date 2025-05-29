```
dfcor(df::AbstractDataFrame, cols1=names(df), cols2=names(df), verbose=false)
```

Compute correlation in a DataFrames by specifying a set of columns `cols1` vs another set `cols2`. The cartesian product of `cols1` and `cols2`'s correlation will be computed
