```julia_skip
@pack! dict_or_typeinstance = a, b, c, ...
```

Pack variables into a mutable composite type, a `Dict{Symbol}`, or a `Dict{String}`.

Example with dict:

```julia
a = 5.0
c = "Hi!"
d = Dict{Symbol,Any}()
@pack! d = a, c
d # Dict{Symbol,Any}(:a=>5.0,:c=>"Hi!")
```

Example with type:

```julia
a = 99
c = "HaHa"
mutable struct A; a; b; c; end
d = A(4,7.0,"Hi")
@pack! d = a, c
d.a == 99 #true
d.c == "HaHa" #true
```

Note that its functionality can be extended by adding methods to the `UnPack.pack!` function.

To "pack" immutables use the package Setfield.jl.
