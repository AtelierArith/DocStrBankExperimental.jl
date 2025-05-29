`canonicalize(template::NamedTuple, input::NamedTuple)`

Canonicalize an input NamedTuple according to a NamedTuple template.   Returns a NamedTuple.

Default values must be specified in `template`.  To avoid specifying   a default value the corresponding item must be a `Type` object, and   its default value will be `missing` (unless overriden in `input`).

# Examples

```julia-repl
julia> template = (xrange=NTuple{2, Number},
                   yrange=NTuple{2, Number},
                   title="Default string");

julia> c = canonicalize(template, (xr=(1,2),))
(xrange = (1, 2), yrange = missing, title = "Default string")

julia> c = canonicalize(template, (xr=(1,2), yrange=(3, 4.), tit="Foo"))
(xrange = (1, 2), yrange = (3, 4.0), title = "Foo")
```
