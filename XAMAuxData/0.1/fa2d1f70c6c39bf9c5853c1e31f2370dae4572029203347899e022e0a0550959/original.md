```
is_well_formed(aux::AbstractAuxiliary) -> Bool
```

Check if the auxiliary is well formed. `AbstractAuxiliary` distinguishes two ways their data can be incorrect: If the data is corrupted such that it is not possible to identify the key, or start/end of the encoded data of the value for a key/value pair, we say the auxiliary is malformed. Accessing values, or iterating such an auxiliary may or may not throw an exception. This notion of malformedness is what this function checks for.

Alternatively, if the keys and encoded values *can* be identified, but the encoded values are corrupt and the value cannot be loaded, we say the auxiliary is invalid. Such auxiliaries can be iterated over, and the values can be loaded, although the loaded value will be of type [`XAMAuxData.Error`](@ref). This can be checked for with `isvalid`. Valid auxiliaries are always well-formed.

# Examples

```jldoctest
julia> aux = SAM.Auxiliary("KM:i:252\tAK::C"); # bad key

julia> is_well_formed(aux)
false

julia> aux["KM"] # loading a value may error
252

julia> aux["AK"] # loading a value may error
ERROR: Invalid SAM tag header. Expected <AuxTag>:<type tag>:, but found no colons.
[...]

julia> aux = SAM.Auxiliary("AB:Z:αβγδ\tCD:f:-1.2"); # bad value encoding

julia> (is_well_formed(aux), isvalid(aux))
(true, false)

julia> aux["AB"] # note: numerical value of enum is not API
InvalidString::Error = 9
```
