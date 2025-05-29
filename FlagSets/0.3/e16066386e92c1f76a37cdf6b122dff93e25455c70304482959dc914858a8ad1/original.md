```
@flagset T [key_1 =] [bit_1 -->] flag_1 [key_2 =] [bit_2 -->] flag_2...
```

Create a [`FlagSet`](@ref) subtype with name `T` and the flags supplied (evaluated). Each instance of the created type represents a subset of `{flag_1, flag_2, ...}`. The associated `bit_1`,`bit_2`, etc, if provided, must be distinct positive powers of 2.

The following constructors are provided:     - `T(itr)`: construct a set of the flags from the given iterable object. Each flag     must be one of `flag_1`, `flag_2`, etc;     - `T()`: construct an empty set;     - `T(bitmask::Integer)`: construct a set of flags associated with each bit in `mask`;     - `T(; kwargs...)`: each `key_i` can be given as a keyword with boolean value     (`key_i = true` includes `flag_i`, `key_i = false` excludes it).

It should be safe to new constructor methods and/or overriding the methods provided (except the default which is defined for the internal struct `FlagSets.BitMask`).

# Examples

```julia
julia> @flagset RoundingFlags begin
    down = RoundDown
    up = RoundUp
    near = 16 --> RoundNearest
    64 --> RoundNearestTiesUp  # No key
end

julia> RoundingFlags([RoundDown,RoundUp])
RoundingFlags with 2 elements:
  RoundingMode{:Down}()
  RoundingMode{:Up}()

julia> RoundingFlags(near = true, up = false, RoundNearestTiesUp = true)
RoundingFlags with 2 elements:
  RoundingMode{:Nearest}()
  RoundingMode{:NearestTiesUp}()

julia> RoundingFlags(1)
RoundingFlags with 1 element:
  RoundingMode{:Down}()

julia> for flag in RoundingFlags(3); println(flag) end
RoundingMode{:Down}()
RoundingMode{:Up}()

julia> RoundingFlags(3) | RoundingFlags(16)
RoundingFlags with 3 elements:
  RoundingMode{:Down}()
  RoundingMode{:Up}()
  RoundingMode{:Nearest}()

julia> eltype(RoundingFlags)
RoundingMode

julia> typemax(RoundingFlags)
RoundingFlags with 4 elements:
  RoundingMode{:Down}()
  RoundingMode{:Up}()
  RoundingMode{:Nearest}()
  RoundingMode{:NearestTiesUp}()

julia> typemin(RoundingFlags)
RoundingFlags([])
```

If some `flag_i` is a `Symbol` and `key_i` is not explicitly given, `key_i` is set to `flag_i`. Therefore, both macros below are equivalent:

```
@flagset FontFlags :bold :italic 8 --> :large
@flagset FontFlags begin
    bold = :bold
    italic = :italic
    large = 8 --> :large
end
```

The following syntaxes can be used to provide `FlagType` and/or `BaseType`:

```julia
@flagset T {FlagType,BaseType} ... # Use supplied types
@flagset T {FlagType} ...          # Detect BaseType
@flagset T {FlagType,_} ...        # Detect BaseType too
@flagset T {_,BaseType} ...        # Detect FlagType
@flagset T {} ...                  # Braces are ignored
```

If `FlagType` is not provided or is `_`, it is inferred from the flag values (like array constructors do). Otherwise, `flag_1`, `flag_2`, etc, must be of type `FlagType`.

If `BaseType` is not provided or is `_`, some convenient integer type is inferred (`UInt32` is used if possible, for maximum compatibility with C code). Otherwise, it must be an `Integer` type big enough to represent each `bit_i`.

Each instance of `T` can be converted to `BaseType`, where each bit set in the converted `BaseType` corresponds to a flag in the flag set. `read` and `write` perform these conversions automatically. In case the flagset is created with a non-default `BaseType`, `Integer(flagset)` will return the integer `flagset` with the type `BaseType`.

```julia
julia> convert(Int, RoundingFlags(up = true, near = true))
6

julia> convert(Integer, RoundingFlags(up = true, near = true))
0x00000006
```

To list flags of a flag set type or instance, use `flags`, e.g.

```julia
julia> flags(RoundingFlags)
(RoundingMode{:Down}(), RoundingMode{:Up}(), RoundingMode{:Nearest}())

julia> flags(RoundingFlags(3))
(RoundingMode{:Down}(), RoundingMode{:Up}())
```

!!! note
    For backward compatibility, the syntax `@flagset T::BaseType ...` is equivalent to `@symbol_flagset T::BaseType ...`, but the former syntax deprecated (use [`symbol_flagset`](@ref) instead).

