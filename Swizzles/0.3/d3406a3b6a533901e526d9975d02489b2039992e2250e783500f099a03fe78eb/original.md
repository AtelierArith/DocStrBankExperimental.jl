```
@swizzle v.xyz
@swizzle v.rgb
@swizzle T v.xyz
@swizzle v[].some.expression().xyz
@swizzle v.xyz = [1, 2, 3]
@swizzle v.rgb = @swizzle v.bgr
@swizzle begin
  a.yz = b.xz
  b.w = a.x
end
```

Perform a swizzling operation, extracting components or, if an assignment is provided, mutating them.

This macro translates `x.<field1><field2>...<fieldn>` field access syntax (e.g. `x.xwyz`) in the provided expression into an appropriate call to [`swizzle`](@ref) (non-mutating) or [`swizzle!`](@ref) (mutating).

An additional type argument `T` may be provided to put the result of a non-mutating swizzle extraction into a specific type (see the documentation for [`swizzle`](@ref) for more details). It has no effect on mutating swizzles.

Each letter on the right-hand side of any `.` is considered as a separate component name, and is by default mapped to:

  * `x` or `r` -> first component
  * `y` or `g` -> second component
  * `z` or `b` -> third component
  * `w` or `a` -> fourth component

using nomenclature from geometry processing (`[x, y, z, w]` representing spatial coordinates) and computer graphics (`[r, g, b, a]` representing color vectors).

This mapping may be customized from Julia 1.11 onwards (see extended help).

# Extended help

From Julia 1.11 onwards, [scoped values](https://docs.julialang.org/en/v1.11-dev/base/scopedvalues/) allow the customization of this component mapping, via `@with Swizzles.component_names => Dict(...)`. For example, if you wanted to consider width, height and depth as first, second and third components, you may do

```julia
new_names = Dict('w' => 1, 'h' => 2, 'd' => 3)

# You might also have done `@with Swizzles.component_names[] => new_names`
# to discard existing names.
@with Swizzles.component_names => merge(Swizzles.component_names[], new_names) begin
  # Note: the `@eval` is important here.
  # It prevents `@swizzle` from being executed before the scoped value is set.
  @eval begin
    @swizzle [10, 20, 30].w
    @swizzle [10, 20, 30].whd
  end
  # `@swizzle` macrocalls in `include`d files will also be affected.
  include("file.jl")
end
```

For convenience, you could even define your own `@swizzle` macro shadowing the one exported by this package as

```julia
using Swizzles

macro _swizzle(ex)
  new_names = Dict('w' => 1, 'h' => 2, 'd' => 3)
  swizzle_ex = @with Swizzles.component_names => merge(Swizzles.component_names[], new_names) begin
    # One might also pass around a `T` parameter as second argument.
    Swizzles.generate_swizzle_expr(ex)
  end
  esc(swizzle_ex)
end

@_swizzle [10, 20, 30].hd
```

Whether or not this is a good idea is for you to decide.
