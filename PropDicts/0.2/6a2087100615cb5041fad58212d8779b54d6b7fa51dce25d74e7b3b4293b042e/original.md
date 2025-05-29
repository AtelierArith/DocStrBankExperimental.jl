```
PropDict <: AbstractDict{Union{Symbol,Int},Any}
```

PropDicts is a dictionary for that supports

Constructors:

```
PropDict(dict::AbstractDict)

PropDict(key1 => value, key2 => value2, ...)
```

During construction, keys are automatically converted to `Symbol`s and `Int`s, values that are dicts are converted to `PropDict`s.

`PropDict` support deep merging:

```julia
x = PropDict(:a => PropDict(:b => 7, :c => 5, :d => 2), :e => "foo")
y = PropDict(:a => PropDict(:c => 42, :d => nothing), :f => "bar")

z = merge(x, y)
@assert z == PropDict(
    :a => PropDict(:b=>7, :d => nothing, :c => 42),
    :e => "foo", :f => "bar"
)

PropDicts.trim_null!(z)
@assert z == PropDict(
    :a => PropDict(:b=>7, :c => 42),
    :e => "foo", :f => "bar"
)
```

Acessing non-existing properties will return instances of [`PropDicts.MissingProperty`](@ref)). When setting the value of missing properties, parent `PropDict`s are created automatically:

```julia
z.foo.bar isa PropDicts.MissingProperty
z.foo.bar = 42
z.foo.bar == 42
```

`PropDict`s can be read/written to/from JSON files using [`readprops`](@ref) and [`writeprops`](@ref).

!!! note
    Like with `Base.Dict`, mutating a `PropDict` is *not* thread safe.

