```
concentration(isotherm::IsothermData; component=nothing, gas_units=:cc, pol_units=:cc)
```

Get the concentrations of a component in the isotherm with specific units. 

# Arguments

  * `gas_units`: Units of the penetrant.

      * Can specify: `:g`, `:cc`

!!! note
    `gas_units` should really be `penetrant_units`, since liquid phase isotherms exist. For now, consider them synonyms.


  * `polymer_units`: Units of the polymer.

      * Can specify: `:g`, `:cc`

For example `concentration(some_isotherm; gas_units=:g, pol_units=:cc)` will get the component concentration in units of $\frac{g}{CC_{polymer}}$

!!! warning
    This method is far from optimized. In fact, every time `concentration` is called, all isotherm components are converted to whatever units were specified. So right now, if performance is critical and all concentrations are required, just get them all at once and iterate as needed.

