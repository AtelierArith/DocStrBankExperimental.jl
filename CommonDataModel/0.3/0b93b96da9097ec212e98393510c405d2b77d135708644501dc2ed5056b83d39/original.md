```
write(dest::AbstractDataset, src::AbstractDataset; include = keys(src), exclude = [])
```

Write the variables of `src` dataset into an empty `dest` dataset (which must be opened in mode `"a"` or `"c"`). The keywords `include` and `exclude` configure which variable of `src` should be included (by default all), or which should be `excluded` (by default none).

If the first argument is a file name, then the dataset is open in create mode (`"c"`).

This function is useful when you want to save the dataset from a multi-file dataset.

To save a subset, one can use the view function `view` to virtually slice a dataset:

## Example

```
NCDataset(fname_src) do ds
    write(fname_slice,view(ds, lon = 2:3))
end
```

All variables in the source file `fname_src` with a dimension `lon` will be sliced along the indices `2:3` for the `lon` dimension. All attributes (and variables without a dimension `lon`) will be copied over unmodified.
