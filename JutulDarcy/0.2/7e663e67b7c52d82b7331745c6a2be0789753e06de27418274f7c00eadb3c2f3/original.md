```
generate_jutuldarcy_examples(
    pth = pwd(),
    name = "jutuldarcy_examples";
    makie = nothing,
    project = true,
    print = true,
    force = false
)
```

Make a copy of all JutulDarcy examples in `pth` in a subfolder `jutuldarcy_examples`. An error is thrown if the folder already exists, unless the `force=true`, in which case the folder will be overwritten and the existing contents will be permanently lost. If `project=true`, a `Project.toml` file will be generated with the same dependencies as that of the doc build system that contains everything needed to run the examples.

The `makie` argument allows replacing the calls to GLMakie in the examples with another backend specified by a `String`. There are no checks performed if the replacement is the name of a valid Makie backend.
