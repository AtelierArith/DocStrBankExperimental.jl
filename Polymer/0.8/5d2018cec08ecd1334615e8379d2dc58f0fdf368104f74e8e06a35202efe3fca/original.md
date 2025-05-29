```
PolymerParameter{T, R} <: AbstractParameter
```

Type represents phyiscal parameters of a polymer system. Each type with a specific T (normally a symbol) defines a parameter. E.g.

````
```julia
PolymerParameter{:ϕ} # define the ϕ parameter
```
````

Pre-defined parameter symbols:

  * χ: Flory-Huggins interaction parameters.
  * N: chain length in number of monomers or Kuhn segments.
  * f: volume fraction of a block in a block copolymer.
  * ϕ: volume fraction of a type of chain in a polymer system.
  * Rg: radius of gyration of a polymer chain.
  * C: chain density C = ρ₀Rg^3/N.
  * b: length of a monomer or a Kuhn segment.
  * α: chain length of a chain with respect to a reference chain.
  * τ: ratio of length of two or more blocks.

Fields

  * `description`: a description of the parameter.
  * `variable_name`: a string representation of the parameter which can be used as Julia variable name.
  * `ascii_label`: a label with pure ascii characters which shall be used for file names, directory names, etc.
  * `plot_label`: a LaTeXStrings used as label for plotting.
  * `value_type`: the number type of the parameter, e.g. integer, float, complex, etc.
  * `allowed_min`: minimum value allowed. If negative infinity, using `typemin(Type)`.
  * `allowed_max`: maximum value allowed. If positive infinity, using `typemax(Type)`.
  * `allowed_values`: only used for discrete finite set. If the allowed values are infinite, use `allowed_min` and `allowed_max` instead.
  * `disallowed_values`: an array of values which are invalid.

User can define their own parameter symbols as long as they also define following two field values. Other fields are deduced automatically from parametric type `T`.

  * `description`
  * `plot_label`
