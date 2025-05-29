```
function render
```

Abstract function. Needs to be specialized by plugins. It is automatically invoked by `Stipple` to serialize a Julia data type (corresponding to the fields in the `ReactiveModel` instance) to JavaScript/JSON. In general the specialized methods should return a Julia `Dict` which are automatically JSON encoded by `Stipple`. If custom JSON serialization is required for certain types in the resulting `Dict`, specialize `JSON.lower` for that specific type.

### Example

```julia
function Stipple.render(ps::PlotSeries, fieldname::Union{Symbol,Nothing} = nothing)
  Dict(:name => ps.name, ps.plotdata.key => ps.plotdata.data)
end
```

#### Specialized JSON rendering for `Undefined`

```julia
JSON.lower(x::Undefined) = "__undefined__"
```
