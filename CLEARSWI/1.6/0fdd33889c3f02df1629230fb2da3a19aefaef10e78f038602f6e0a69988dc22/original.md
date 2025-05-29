```
Options(;   mag_combine=:SNR,
            mag_sens=nothing,
            mag_softplus=true,
            phase_unwrap=:laplacian,
            phase_hp_sigma=[4,4,0],
            phase_scaling_type=:tanh,
            phase_scaling_strength=4,
            writesteps=nothing)
```

  * `mag_combine` selects the echo combination for the magnitude. Options are 

      * `:SNR`
      * `:average`
      * `:last` to select the last echo
      * `(:CNR => (:gm, :wm))` to optimize the contrast between two selected tissues with the possible tissues classes to select in `src/tissue.jl`, currently only working for 7T
      * `(:echo => 3)` to select the 3rd echo
      * `(:closest => 15.3)` to select the echo that is closest to 15.3 ms
      * `(:SE => 15.3)` to simulate the contrast that would be achieved using a corresponding single-echo scan with 15.3 ms echo time.
  * If `mag_sens` is set to an array, it is used instead of CLEAR-SWI sensitivity estimation. This can also be set to `mag_sens=[1]` to use the constant sensitivity of 1 and effectively avoid sensitivity correction. To change the sigma*mm value of the expected bias field size, set it to i.e. `mag*sens=(:sigma_mm => 7)`. The default is 7mm.
  * To deactivate scaling of the combined magnitude with the softplus function, use `mag_softplus=false`.
  * `phase_unwrap` is either `:laplacian`, `:romeo`, or `:laplacianslice` (slicewise laplacian unwrapping)
  * The `phase_hp_sigma` is used for high-pass filtering and is given in voxel for the [x,y,z]-dimension.
  * `phase_scaling_type` is the scaling function to create the phase mask and can be `:tanh` or `:negativetanh` for sigmoidal filtering, or `:positive`, `:negative`, and `:triangular` for traditional SWI application.
  * `phase_scaling_strength` adjusts the strength of the created phase mask. A higher `phase_scaling_strength` is a stronger phase appearance. With a traditional SWI `phase_scaling_type` it corresponds to the power or number of phase mask multiplications.
  * Set `writesteps` to the path, where intermediate steps should be saved, e.g. `writesteps="/tmp/clearswi_steps"`. If set to `nothing`, intermediate steps won't be saved.
  * Set `qsm` to true
