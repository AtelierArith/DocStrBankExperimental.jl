```
find_catnum_columns(instances::DataFrame,maxuniqcat::Int=0)
```

Finds all categorial and numerical columns. Categorical columns are those that do not have Real type nor do all their elements correspond to Real. Also, columns with size of unique instances are less than `maxuniqcat` are considered categorical.
