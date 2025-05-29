`charnames(ComplexReflectionGroup or Spets;options...)` `charnames(io::IO,ComplexReflectionGroup or Spets)`

returns  the list of character names for the reflection group or Spets `W`. The  options may imply  alternative names in  certain cases, or a different formatting of names in general. They can be specified by `IO` attributes if giving an `IO` as argument.

```julia-repl
julia> W=coxgroup(:G,2)
G₂

julia> charnames(W;limit=true)
6-element Vector{String}:
 "φ₁‚₀"
 "φ₁‚₆"
 "φ′₁‚₃"
 "φ″₁‚₃"
 "φ₂‚₁"
 "φ₂‚₂"

julia> charnames(W;TeX=true)
6-element Vector{String}:
 "\phi_{1,0}"
 "\phi_{1,6}"
 "\phi_{1,3}'"
 "\phi_{1,3}''"
 "\phi_{2,1}"
 "\phi_{2,2}"

julia> charnames(W;spaltenstein=true,limit=true)
6-element Vector{String}:
 "1"
 "ε"
 "εₗ"
 "ε_c"
 "θ′"
 "θ″"

julia> charnames(W;spaltenstein=true,TeX=true)
6-element Vector{String}:
 "1"
 "\varepsilon"
 "\varepsilon_l"
 "\varepsilon_c"
 "\theta'"
 "\theta''"
```

The  last two  commands show  the character  names used by Spaltenstein and Lusztig when describing the Springer correspondence.
