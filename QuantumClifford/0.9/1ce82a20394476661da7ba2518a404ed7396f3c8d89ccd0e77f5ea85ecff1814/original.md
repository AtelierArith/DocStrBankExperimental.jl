```julia
canonicalize!(
    state::QuantumClifford.AbstractStabilizer;
    phases,
    ranks
) -> Union{Tuple{QuantumClifford.AbstractStabilizer, Int64, Int64}, QuantumClifford.AbstractStabilizer}

```

Canonicalize a stabilizer (in place).

Assumes the input is a valid stabilizer (all operators commute and have real phases). It permits redundant generators and identity generators.

```jldoctest
julia> ghz = S"XXXX
               ZZII
               IZZI
               IIZZ";


julia> canonicalize!(ghz)
+ XXXX
+ Z__Z
+ _Z_Z
+ __ZZ

julia> canonicalize!(S"XXXX
                       IZZI
                       IIZZ")
+ XXXX
+ _Z_Z
+ __ZZ
```

Not all rows in the tableau in the next example are independent:

```jldoctest
julia> canonicalize!(S"XXXX
                       ZZII
                       IZZI
                       IZIZ
                       IIZZ")
+ XXXX
+ Z__Z
+ _Z_Z
+ __ZZ
+ ____
```

In cases of lower rank, more advanced tableau structures might be better. For instance the [`MixedStabilizer`](@ref) or [`MixedDestabilizer`](@ref) structures (you can read more about them in the [Data Structures section](@ref Choosing-Appropriate-Data-Structure) of the documentation).

If `phases=false` is set, the canonicalization does not track the phases in the tableau, leading to significant (constant factor) speedup.

```jldoctest
julia> s = S"-ZX
              XZ"
- ZX
+ XZ

julia> canonicalize!(copy(s), phases=false)
- XZ
+ ZX

julia> canonicalize!(copy(s))
+ XZ
- ZX
```

If `ranks=true` is set, the last pivot indices for the X and Z stage of the canonicalization are returned as well.

```jldoctest
julia> s = S"XXXX
             ZZII
             IZIZ
             ZIIZ";


julia> _, ix, iz = canonicalize!(s, ranks=true); ix, iz
(1, 3)

julia> s
+ XXXX
+ Z__Z
+ _Z_Z
+ ____
```

Based on [garcia2012efficient](@cite).

See also: [`canonicalize_rref!`](@ref), [`canonicalize_gott!`](@ref)
