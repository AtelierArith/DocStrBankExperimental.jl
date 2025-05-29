```
FortranString{CharType}
```

Datatype for emulating FORTRAN `CHARACTER*N` strings.

This type is a wrapper for a `Vector` with elements of type `CharType`. Some functions and broadcasting added for limited strings emulation.

Assignment should be done via broadcasting:

```jldoctest
julia> s = F8"abc"; s .= "AB" * F"CD"; s
F8"ABC"

julia> s = F"abc"; s[2:end] .= "ABC"; s
F"aAB"
```

Element-wise assignment is also supported, but it is not FORTRAN alike. Element comparison

```jldoctest
julia> s = F8"abc"; s[1:1] == 'a'
true

julia> s = F8"abc"; (s[1:1] == 'a', s[2:2] == "b")
(true, true)
```

See also `@F_str` for quoting.
