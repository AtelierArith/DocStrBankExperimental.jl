```
build(path::String) -> BSTModel
```

This function is used to build a `BSTModel` object from a model file. The model file can be in one of the following formats: `bst, txt, jld2, dat, net, toml`. The function will parse the file and build the model object.

### Arguments

  * `path::String`: The path to the model file.

### Returns

  * A `BSTModel` object. See the `BSTModel` documentation for more information on the fields of the model object.
