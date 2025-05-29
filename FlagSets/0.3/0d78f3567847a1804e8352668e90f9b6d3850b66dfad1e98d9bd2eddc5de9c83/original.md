```
@symbol_flagset T[::BaseType] flag_1[=bit_1] flag_2[=bit_2] ...
```

Create a `FlagSet{Symbol,BaseType}` subtype with name `T` and the flags supplied. Each instance of `T` represents a subset of `{:flag1, :flag2, ...}`. The associated `bit_1`,`bit_2`, etc, if provided, must be distinct positive powers of 2.

The following constructors are provided:     - `T(itr)`: construct a set of the symbols from the given iterable object. Each symbol     must be one of :`flag_1`, :`flag_2`, etc;     - `T()`: construct an empty set;     - `T(sym1::Symbol, syms::Symbol...)`: equivalent to `T([sym1, syms...])`     - `T(bitmask::Integer)`: construct a set of flags associated with each bit in `mask`;     - `T(; kwargs...)`: each `flag_i` can be supplied as a boolean value     (`flag_i = true` includes `:flag_i`, `flag_i = false` excludes it).

It should be safe to new constructor methods and/or overriding the methods provided (except the default using an internal struct, i.e., `T(::FlagSets.BitMask)`).

To construct sets of non-`Symbol` constants, use the macro [`@flagset`](@ref).

# Examples

```julia
julia> @symbol_flagset FontFlags bold=1 italic=2 large=4

julia> FontFlags(1)
FontFlags with 1 element:
  :bold

julia> FontFlags(:bold, :italic)
FontFlags with 2 elements:
  :bold
  :italic

julia> FontFlags(bold=true, italic=false)
FontFlags with 1 element:
  :bold

julia> for flag in FontFlags(3); println(flag) end
bold
italic

julia> FontFlags(3) | FontFlags(4)
FontFlags with 3 elements:
  :bold
  :italic
  :large

julia> eltype(FontFlags)
Symbol

julia> typemax(FontFlags)
FontFlags with 3 elements:
  :bold
  :italic
  :large

julia> typemin(FontFlags)
FontFlags([])
```

Values can also be specified inside a `begin` block, e.g.

```julia
@symbol_flagset T begin
    flag_1 [= x]
    flag_2 [= y]
end
```

If `BaseType` is provided, it must be an `Integer` type big enough to represent each `bit_i`. Otherwise, some convenient integer type is inferred (`UInt32` is used if possible, to guarantee compatibility with C code). Each instance of `T` can be converted to `BaseType`, where each bit set in the converted `BaseType` corresponds to a flag in the flag set. `read` and `write` perform these conversions automatically. In case the flagset is created with a non-default `BaseType`, `Integer(flagset)` will return the integer `flagset` with the type `BaseType`.

```julia
julia> convert(Int, FontFlags(bold=true, italic=false))
1

julia> convert(Integer, FontFlags(bold=true, italic=false))
0x00000001
```

To list flags of a flag set type or instance, use `flags`, e.g.

```julia
julia> flags(FontFlags)
(:bold, :italic, :large)

julia> flags(FontFlags(3))
(:bold, :italic)
```
