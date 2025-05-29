```
TNT(::DataFrame; optional-args)
```

Extracts target and non-target scores from a dataframe.  

The optional arguments encode which colums are used for what purpose. 

  * `score` (default `:score`) is the name of the column containing the classifier's scores.
  * `target` (default `:target`), of type `Bool`, determines whether this is a target score or not.
