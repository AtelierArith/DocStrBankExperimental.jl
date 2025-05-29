```
format_A_X(default_metals_H, default_alpha_H, abundances; kwargs... )
```

Returns a 92 element vector containing abundances in $A(X)$ ($\log_{10}(X/H) + 12$) format for elements from hydrogen to uranium.

# Arguments

You can specify abundance with these positional arguments.  All are optional, but if `default_alpha_H` is provided, `default_metals_H` must be as well.

  * `default_metals_H` (default: 0), i.e. [metals/H] is the $\log_{10}$ solar-relative abundance of elements heavier than He. It is overridden by `default_alpha` and `abundances` on a per-element basis.
  * `default_alpha_H` (default: same as `default_metals_H`), i.e. [alpha/H] is the $\log_{10}$ solar-relative abundance of the alpha elements (See `alpha_elements`, below). It is overridden by `abundances` on a per-element basis.
  * `abundances` is a `Dict` mapping atomic numbers or symbols to [$X$/H] abundances.  (Set `solar_relative=false` to use $A(X)$ abundances instead.) These override `default_metals_H`. This is the only way to specify an abundance of He that is non-solar.

# Keyword arguments

  * `solar_relative` (default: true): When true, interpret abundances as being in [$X$/H] ($\log_{10}$ solar-relative) format.  When false, interpret them as $A(X)$ abundances, i.e. $A(x) = \log_{10}(n_X/n_\mathrm{H}) + 12$, where $n_X$ is the number density of $X$. Note that abundances not specified default to the solar value still depend on the solar value, as they are set according to `default_metals_H` and `default_alpha_H`.
  * `solar_abundances` (default: `Korg.asplund_2020_solar_abundances`) is the set of solar abundances to use, as a vector indexed by atomic number. `Korg.asplund_2009_solar_abundances` and `Korg.grevesse_2007_solar_abundances` are also provided for convenience.
  * `alpha_elements` (default: [`Korg.default_alpha_elements`](@ref)): vector of atomic numbers of the alpha elements. (Useful since conventions vary.)
