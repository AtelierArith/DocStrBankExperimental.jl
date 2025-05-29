```
convert_unit(value::Real, unit1::Symbol, unit2::Symbol)
```

Convert the energy `value` from `unit1` to `unit2`. The `unit1` and `unit2` can be either the following `Symbol`:

  * `:J` : Joule
  * `:eV` : electron volt
  * `:meV` : milli-electron volt
  * `:MHz` : Mega-Hertz multiplied by Planck constant $h$
  * `:GHz` : Giga-Hertz multiplied by Planck constant $h$
  * `:K` : Kelvin multiplied by Boltzmann constant $k$
  * `:mK` : milli-Kelvin multiplied by Boltzmann constant $k$

Note that we use the values stored in [`PhysicalConstants`](@ref) to do the conversion.

# Examples

```jldoctest
julia> convert_unit(1, :eV, :J)
1.602176634e-19

julia> convert_unit(1, :GHz, :J)
6.62607015e-25

julia> round(convert_unit(1, :meV, :mK), digits=4)
11604.5181
```
