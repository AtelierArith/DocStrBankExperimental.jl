A custom "weakref" string type that only points to external string data. Allows for the creation of a "string" instance without copying data, which allows for more efficient string parsing/movement in certain data processing tasks.

**Please note that no original reference is kept to the parent string/memory, so `WeakRefString` becomes unsafe once the parent object goes out of scope (i.e. loses a reference to it)**

Internally, a `WeakRefString{T}` holds:

  * `ptr::Ptr{T}`: a pointer to the string data (code unit size is parameterized on `T`)
  * `len::Int`: the number of code units in the string data

See also [`StringArray`](@ref)
