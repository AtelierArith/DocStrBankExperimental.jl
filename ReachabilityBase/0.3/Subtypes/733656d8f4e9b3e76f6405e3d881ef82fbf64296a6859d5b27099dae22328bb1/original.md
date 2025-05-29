```
subtypes(atype, concrete::Bool)
```

Return the subtypes of a given abstract type.

### Input

  * `atype`    – an abstract type
  * `concrete` – if `true`, only return the concrete subtypes (leaves of the type               hierarchy); otherwise return only the direct subtypes

### Output

A list with the subtypes of the abstract type `atype`, sorted alphabetically.

### Examples

Consider the `Integer` type. If we pass `concrete = false`, the implementation imitates `Base.subtypes` without any arguments.

```jldoctest subtypes
julia> using ReachabilityBase.Subtypes

julia> subtypes(Integer, false)
3-element Vector{Any}:
 Bool
 Signed
 Unsigned
```

If we pass `concrete = true`, we obtain the concrete subtypes instead.

```jldoctest subtypes
julia> subtypes(Integer, true)
12-element Vector{Type}:
 BigInt
 Bool
 Int128
 Int16
 Int32
 Int64
 Int8
 UInt128
 UInt16
 UInt32
 UInt64
 UInt8
```
