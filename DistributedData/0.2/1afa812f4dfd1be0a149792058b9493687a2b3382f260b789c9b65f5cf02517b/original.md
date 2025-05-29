```
dapply_cols(dInfo::Dinfo, fn, columns::Vector{Int})
```

Apply a function `fn` over columns of a distributed dataset.

`fn` gets *2* parameters:

  * a data vector for (the whole column saved at one worker)
  * index of the column in the `columns` array (i.e. a number from `1:length(columns)`)
