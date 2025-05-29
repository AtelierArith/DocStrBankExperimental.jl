```
runMC(param::Parameter)
runMC(params::AbstractArray{Parameter}
      ;
      parallel::Bool=false,
      autoID::Bool=true)
```

Runs Monte Carlo simulation(s) and returns calculated observables.

# Restart

If a checkpoint file named `"$(param["Checkpoint Filename Prefix"])_$(param["ID"]).dat"` exists and `param["Checkpoint Interval"] > 0.0`, `runMC` loads this file and restarts the pending simulation. NOTE: Restart will fail if the version or the system image of julia change (see the doc of `Serialization.serialize` ).

# Keyward arguments

  * `autoID`: If true, `"ID"`s will be set (overwritten) as `params[i]["ID"] = i`.
  * `parallel`: If true, runs simulations in parallel (uses `pmap` instead of `map`).

# Required keys in `param`

  * "Model"
  * "Lattice"
  * "Update Method"

# Optional keys in `param`

  * "MCS": The number of Monte Carlo steps after thermalization

      * Default: `8192`
  * "Thermalization": The number of Monte Carlo steps for thermalization

      * Default: `MCS>>3`
  * "Binning Size": The size of binning

      * Default: `0`
  * "Number of Bins": The number of bins

      * Default: `0`
      * If both "Binning Size" and "Number of Bins" are not given, "Binning Size" is set to `floor(sqrt(MCS))`.
  * "Seed": The initial seed of the random number generator, `MersenneTwister`

      * Default: determined randomly (see the doc of `Random.seed!`)
  * "Checkpoint Filename Prefix": See the "Restart" section.

      * Default: `"cp"`
  * "ID": See the "Restart" section.

      * Default: `0`
  * "Checkpoint Interval": Time interval between writing checkpoint file in seconds.

      * Default: `0.0`, this means that NO checkpoint file will be loaded and saved.
