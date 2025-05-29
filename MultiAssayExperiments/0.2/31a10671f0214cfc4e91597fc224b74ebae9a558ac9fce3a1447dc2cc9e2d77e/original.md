```
setsampledata!(x, value)
```

Set the sample data in the `MultiAssayExperiment` `x` to the `DataFrame` `value`.

The returned object should contain `name` as the first column, containing a vector of unique strings. If `check = true`, the function will check the validity of the sample data before returning it.

# Examples

```jldoctest
julia> using MultiAssayExperiments

julia> x = MultiAssayExperiments.exampleobject();

julia> sd = copy(sampledata(x));

julia> sd[!,"stuff"] = [rand() for i in 1:size(sd)[1]];

julia> setsampledata!(x, sd);

julia> names(sampledata(x))
3-element Vector{String}:
 "name"
 "disease"
 "stuff"
```
