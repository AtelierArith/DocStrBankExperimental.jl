```
@logscale(symb,abbr,name,base,prefactor,irp)
```

Define a logarithmic scale. Unlike with units, there is no special treatment for power-of-ten prefixes (decibels and bels are defined separately). However, arbitrary bases are possible, and computationally appropriate `log` and `exp` functions are used in calculations when available (e.g. `log2`, `log10` for base 2 and base 10, respectively).

This macro defines a `MixedUnits` object identified by symbol `symb`. This can be used to construct `Gain` types, e.g. `3*dB`. Additionally, two other `MixedUnits` objects are defined, with symbols `Symbol(symb,"_rp")` and `Symbol(symb,"_p")`, e.g. `dB_rp` and `dB_p`, respectively. These objects serve nearly the same purpose, but have extra information in their type that indicates whether they should be considered as root-power ratios or power ratios upon conversion to pure numbers.

This macro also defines another macro available as `@symb`. For example, `@dB` in the case of decibels. This can be used to construct `Level` objects at parse time. Usage is like `@dB 3V/1V`.

`prefactor` is the prefactor out in front of the logarithm for this log scale. In all cases it is defined with respect to taking ratios of power quantities. Just divide by two if you want to refer to root-power / field quantities instead.

`irp` (short for "is root power?") specifies whether the logarithmic scale is defined with respect to ratios of power or root-power quantities. In short: use `false` if your scale is decibel-like, or `true` if your scale is neper-like.

Examples:

```jldoctest
julia> using Unitful: V, W

julia> @logscale dΠ "dΠ" Decipies π 10 false
dΠ

julia> @dΠ π*V/1V
20.0 dΠ (1 V)

julia> dΠ(π*V, 1V)
20.0 dΠ (1 V)

julia> @dΠ π^2*V/1V
40.0 dΠ (1 V)

julia> @dΠ π*W/1W
10.0 dΠ (1 W)
```
