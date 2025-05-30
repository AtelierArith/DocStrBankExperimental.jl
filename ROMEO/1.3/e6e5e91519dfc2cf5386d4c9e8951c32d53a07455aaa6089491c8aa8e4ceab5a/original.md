```
unwrap(wrapped::AbstractArray; keyargs...)
```

ROMEO unwrapping for 3D and 4D data.

### Optional keyword arguments:

  * `TEs`: Required for 4D data. The echo times for multi-echo data. In the case of single-echo    application with phase and the phase2 as a tuple (eg. (5, 10) or [5, 10]).
  * `weights`: Options are [`:romeo`] | `:romeo2` | `:romeo3` | `:bestpath`.
  * `mag`: The magnitude is used to improve the unwrapping-path.
  * `mask`: Unwrapping is only performed inside the mask.
  * `phase2`: A second reference phase image (possibly with different echo time).   It is used for calculating the phasecoherence weight. This is automatically   done for 4D multi-echo input and therefore not required.
  * `correctglobal=false`: If `true` corrects global n2π offsets.
  * `individual=false`: If `true` perform individual unwrapping of echos.   Type `?unwrap_individual` for more information
  * `template=1`: echo that is spatially unwrapped (if `individual` is `false`)
  * `maxseeds=1`: higher values allow more seperate regions
  * `merge_regions=false`: spatially merge neighboring regions after unwrapping
  * `correct_regions=false`: bring each regions median closest to 0 by adding n2π
  * `wrap_addition=0`: [0;π], allows 'linear unwrapping', neighbors can have more   (π+wrap_addition) phase difference
  * `temporal_uncertain_unwrapping=0.5`: Useful for veins. It uses spatial   unwrapping on voxels that have high uncertainty values after temporal   unwrapping. A higher quality threshold re-unwraps more voxels spatially.

# Examples

```julia-repl
julia> using MriResearchTools
julia> phase = readphase("phase_3echo.nii")
julia> unwrapped = unwrap(phase; TEs=[1,2,3])
julia> savenii(unwrapped, "unwrapped.nii"; header=header(phase))
```
