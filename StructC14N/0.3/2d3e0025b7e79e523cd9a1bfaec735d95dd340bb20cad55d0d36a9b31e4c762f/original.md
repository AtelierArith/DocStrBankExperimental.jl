`canonicalize(template, input::Tuple)`

Canonicalize an input tuple according to a template.  Returns a   NamedTuple or a structure instance according to the type of   `template`.  The input tuple must have same number of elements as   the template.

# Examples

```julia-repl
julia> template = (xrange=NTuple{2,Number},
                   yrange=NTuple{2,Number},
                   title="Default string");

julia> canonicalize(template, ((1,2), (3, 4.), "Foo"))
(xrange = (1, 2), yrange = (3, 4.0), title = "Foo")

julia> struct AStruct
           xrange::NTuple{2, Number}
           yrange::NTuple{2, Number}
           title::Union{Missing, String}
       end;

julia> canonicalize(AStruct, ((1,2), (3, 4.), "Foo"))
AStruct((1, 2), (3, 4.0), "Foo")

julia> template = AStruct((0,0), (0.,0.), missing);

julia> canonicalize(template, ((1,2), (3, 4.), "Foo"))
AStruct((1, 2), (3, 4.0), "Foo")
```
