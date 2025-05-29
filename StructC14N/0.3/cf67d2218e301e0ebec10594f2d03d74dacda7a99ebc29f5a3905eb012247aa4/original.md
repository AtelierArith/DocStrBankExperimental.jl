`canonicalize(template::DataType, input::NamedTuple)`

Canonicalize an input NamedTuple according to a template in a   structure definition.  Returns a structure instance.

If `input` contains less values than required in the template an   attempt will be made to create a structure with `missing` values.   If this is forbidden by the structure definition an error is raised.

# Examples

```julia-repl
julia> struct AStruct
           xrange::NTuple{2, Number}
           yrange::NTuple{2, Number}
           title::Union{Missing, String}
       end

julia> canonicalize(AStruct, (xr=(1,2), yr=(3,4.)))
AStruct((1, 2), (3, 4.0), missing)

julia> canonicalize(AStruct, (xr=(1,2), yr=(3,4.), tit="Foo"))
AStruct((1, 2), (3, 4.0), "Foo")
```
