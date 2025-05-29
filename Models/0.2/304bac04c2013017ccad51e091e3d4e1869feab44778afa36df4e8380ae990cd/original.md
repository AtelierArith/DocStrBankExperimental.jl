```
submodels(::Union{Template, Model})
```

Return all submodels within a multistage model/template.

Submodels are models within a model that have their own inputs (which may or may not be combined with outputs of *earlier* submodels, before actually being passed as input to the submodel). Such multistage models take a tuple of inputs (which may be nested if the submodel itself has submodels). The order of submodels returned by `submodels` is as per the order of the inputs in the tuple.

For single-stage models, (i.e. ones that simply take a matrix as input), this returns an empty tuple. Wrapper models which do not expose their inner models to seperate inputs, including ones that only wrap a single model, should **not** define `submodels` as they are (from the outside API perspective) single-stage models.
