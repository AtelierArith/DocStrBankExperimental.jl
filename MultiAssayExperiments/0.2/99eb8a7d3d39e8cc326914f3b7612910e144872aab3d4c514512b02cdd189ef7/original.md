```
setsamplemap!(x, value)
```

Set the sample mapping in the `MultiAssayExperiment` `x` to a `DataFrame` `value`. This returns a reference to the modified `x`.

`value` should contain the `sample`, `experiment` and `colname` columns in that order. Each column should contain a vector of strings:

  * Values of `sample` may (but are not required to) correspond to the names of samples in `sampledata(x)`.
  * Values of `experiment` may (but are not required to) correspond to the keys of `experiments(x)`.
  * Values of `colname` should (but are not required to) correspond to the columns of the corresponding `SummarizedExperiment` in the `experiment` of the same row.

This correspondence is used for convenient subsetting and extraction, e.g., [`expandsampledata`](@ref), [`filtersamplemap`](@ref). However, values in the sample mapping columns need not have a 1:1 match to their corresponding target;  any values unique to one or the other will be ignored in the relevant methods. This allows users to flexibly manipulate the object without constantly hitting validity checks.

It is legal (but highly unusual) for a given combination of `experiment` and `colname` to occur more than once. This may incur warnings in methods like [`expandsampledata`](@ref).

# Examples

```jldoctest
julia> using MultiAssayExperiments

julia> x = MultiAssayExperiments.exampleobject();

julia> y = samplemap(x)[1:10,:];

julia> setsamplemap!(x, y);

julia> size(samplemap(x))[1]
10
```
