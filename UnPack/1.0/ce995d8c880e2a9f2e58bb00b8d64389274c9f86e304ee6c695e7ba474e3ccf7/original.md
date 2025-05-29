```julia_skip
@unpack a, b, c, ... = dict_or_typeinstance
```

Unpack fields/properties/keys from a composite type, a `Dict{Symbol}`, a `Dict{String}`, or a module into variables.

Example with dict:

```julia
d = Dict{Symbol,Any}(:a=>5.0,:b=>2,:c=>"Hi!")
@unpack a, c = d
a == 5.0 #true
c == "Hi!" #true
```

Example with type:

```julia
struct A; a; b; c; end
d = A(4,7.0,"Hi")
@unpack a, c = d
a == 4 #true
c == "Hi" #true
```

Note that its functionality can be extended by adding methods to the `UnPack.unpack` function.
