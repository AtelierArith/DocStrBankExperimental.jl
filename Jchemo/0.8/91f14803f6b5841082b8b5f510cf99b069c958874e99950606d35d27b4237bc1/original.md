```
plotconf(object; size = (500, 400), cnt = true, ptext = true, 
    fontsize = 15, coldiag = :red, )
```

Plot a confusion matrix.

  * `object` : Output of function `conf`.

Keyword arguments:

  * `size` : Size (horizontal, vertical) of the figure.
  * `cnt` : Boolean. If `true`, plot the occurrences,    else plot the row %s.
  * `ptext` : Boolean. If `true`, display the value in each cell.
  * `fontsize` : Font size when `ptext = true`.
  * `coldiag` : Font color when `ptext = true`.

See examples in help page of function `conf`. ```
