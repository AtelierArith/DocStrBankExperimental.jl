```
@varname(expr, concretize=false)
```

A macro that returns an instance of [`VarName`](@ref) given a symbol or indexing expression `expr`.

If `concretize` is `true`, the resulting expression will be wrapped in a `concretize()` call.

Note that expressions involving dynamic indexing, i.e. `begin` and/or `end`, will always need to be concretized as `VarName` only supports non-dynamic indexing as determined by `is_static_optic`. See examples below.

## Examples

### Dynamic indexing

```jldoctest
julia> x = (a = [1.0 2.0; 3.0 4.0; 5.0 6.0], );

julia> @varname(x.a[1:end, end][:], true)
x.a[1:3, 2][:]

julia> @varname(x.a[end], false)  # disable concretization
ERROR: LoadError: Variable name `x.a[end]` is dynamic and requires concretization!
[...]

julia> @varname(x.a[end])  # concretization occurs by default if deemed necessary
x.a[6]

julia> # Note that "dynamic" here refers to usage of `begin` and/or `end`,
       # _not_ "information only available at runtime", i.e. the following works.
       [@varname(x.a[i]) for i = 1:length(x.a)][end]
x.a[6]

julia> # Potentially surprising behaviour, but this is equivalent to what Base does:
       @varname(x[2:2:5]), 2:2:5
(x[2:2:4], 2:2:4)
```

### General indexing

Under the hood `optic`s are used for the indexing:

```jldoctest
julia> getoptic(@varname(x))
identity (generic function with 1 method)

julia> getoptic(@varname(x[1]))
(@o _[1])

julia> getoptic(@varname(x[:, 1]))
(@o _[Colon(), 1])

julia> getoptic(@varname(x[:, 1][2]))
(@o _[Colon(), 1][2])

julia> getoptic(@varname(x[1,2][1+5][45][3]))
(@o _[1, 2][6][45][3])
```

This also means that we support property access:

```jldoctest
julia> getoptic(@varname(x.a))
(@o _.a)

julia> getoptic(@varname(x.a[1]))
(@o _.a[1])

julia> x = (a = [(b = rand(2), )], ); getoptic(@varname(x.a[1].b[end], true))
(@o _.a[1].b[2])
```

Interpolation can be used for variable names, or array name, but not the lhs of a `.` expression. Variables within indices are always evaluated in the calling scope.

```jldoctest
julia> name, i = :a, 10;

julia> @varname(x.$name[i, i+1])
x.a[10, 11]

julia> @varname($name)
a

julia> @varname($name[1])
a[1]

julia> @varname($name.x[1])
a.x[1]

julia> @varname(b.$name.x[1])
b.a.x[1]
```
