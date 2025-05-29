```
v = cfvariable(ds::NCDataset,varname::SymbolOrString; <attrib> = <value>)
```

Return the variable `varname` in the dataset `ds` as a `NCDataset.CFVariable`. The keyword argument `<attrib>` are the attributes (`fillvalue`, `missing_value`, `scale_factor`, `add_offset`, `units` and `calendar`) relevant to the CF conventions. By specifing the value of these attributes, the one can override the value specified in the data set. If the attribute is set to `nothing`, then the attribute is not loaded and the corresponding transformation is ignored. This function is similar to `ds[varname]` with the additional flexibility that some variable attributes can be overridden.

Example:

```julia
NCDataset("foo.nc","c") do ds
  defVar(ds,"data",[10., 11., 12., 13.], ("time",), attrib = Dict(
      "add_offset" => 10.,
      "scale_factor" => 0.2))
end

# The stored (packed) valued are [0., 5., 10., 15.]
# since 0.2 .* [0., 5., 10., 15.] .+ 10 is [10., 11., 12., 13.]

ds = NCDataset("foo.nc");

@show ds["data"].var[:]
# returns [0., 5., 10., 15.]

@show cfvariable(ds,"data")[:]
# returns [10., 11., 12., 13.]

# neither add_offset nor scale_factor are applied
@show cfvariable(ds,"data", add_offset = nothing, scale_factor = nothing)[:]
# returns [0, 5, 10, 15]

# add_offset is applied but not scale_factor
@show cfvariable(ds,"data", scale_factor = nothing)[:]
# returns [10, 15, 20, 25]

# 0 is declared as the fill value (add_offset and scale_factor are applied as usual)
@show cfvariable(ds,"data", fillvalue = 0)[:]
# return [missing, 11., 12., 13.]

# Use the time units: days since 2000-01-01
@show cfvariable(ds,"data", units = "days since 2000-01-01")[:]
# returns [DateTime(2000,1,11), DateTime(2000,1,12), DateTime(2000,1,13), DateTime(2000,1,14)]

close(ds)
```
