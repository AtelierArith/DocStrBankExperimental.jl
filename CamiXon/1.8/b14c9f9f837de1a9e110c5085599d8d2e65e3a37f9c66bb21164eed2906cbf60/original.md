```
dictCoreConfiguration
```

Closed-shell configuration for the elements in the periodic table.

```
julia> dictCoreConfiguration
Dict{String, String} with 15 entries:
  "[Ne]" => "1s²2s²2p⁶"
  "[Cd]" => "1s²2s²2p⁶3s²3p⁶3d¹⁰4s²4p⁶5s²4d¹⁰"
  "[Sr]" => "1s²2s²2p⁶3s²3p⁶3d¹⁰4s²4p⁶5s²"
  "[Yb]" => "1s²2s²2p⁶3s²3p⁶3d¹⁰4s²4p⁶5s²4d¹⁰5p⁶6s²4f¹⁴"
  "[Mg]" => "1s²2s²2p⁶3s²"
  "[Ba]" => "1s²2s²2p⁶3s²3p⁶3d¹⁰4s²4p⁶5s²4d¹⁰5p⁶6s²"
  "[Xe]" => "1s²2s²2p⁶3s²3p⁶3d¹⁰4s²4p⁶5s²4d¹⁰5p⁶"
  ⋮  => ⋮
```

#### Examples:

```
julia> dict = dictCoreConfiguration;

julia> get(dict, "[Yb]", nothing)
"1s²2s²2p⁶3s²3p⁶3d¹⁰4s²4p⁶5s²4d¹⁰5p⁶6s²4f¹⁴"
```
