```
near_source_saturation(m, sat::NearSourceSaturationParameters)
```

Near-source saturation term. Used to create equivalent point-source distance. Switches methods based upon `sat.model`.

# Arguments

Options for `sat.model` are:

  * `:BT15` for Boore & Thompson (2015) finite fault factor
  * `:YA15` for Yenier & Atkinson (2014) finite fault factor
  * `:CY14` for a model fitted to the Chiou & Youngs (2014) saturation lengths (over all periods)
  * `:SEA21` for the Stafford et al. (2021) saturation model obtained from inversion of Chiou & Youngs (2014)
  * `:None` for zero saturation length
  * `:ConstantConstrained` for a constant value, `sat.hconi[1]`, not subject to AD operations
  * `:ConstantVariable` for a constant value, `sat.hvari[1]`, that is subject to AD operations

Any other symbol passed will return `NaN`.

See also: [`near_source_saturation`](@ref)
