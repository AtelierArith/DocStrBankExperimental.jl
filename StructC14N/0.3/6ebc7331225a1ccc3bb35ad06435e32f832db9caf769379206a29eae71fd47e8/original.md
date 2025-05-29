`canonicalize(template, input::NamedTuple)`

Canonicalize an input NamedTuple according to a template in a   structure instance.  Returns a structure instance.

All values in the template are taken as default values.

# Examples

```julia-repl
julia> struct AStruct
           xrange::NTuple{2, Number}
           yrange::NTuple{2, Number}
           title::Union{Missing, String}
       end

julia> template = AStruct((0,0), (0.,0.), missing);

julia> canonicalize(template, (xr=(1,2),))
AStruct((1, 2), (0.0, 0.0), missing)

julia> canonicalize(template, (yr=(1,2), xr=(3.3, 4.4), tit="Foo"))
AStruct((3.3, 4.4), (1, 2), "Foo")
```
