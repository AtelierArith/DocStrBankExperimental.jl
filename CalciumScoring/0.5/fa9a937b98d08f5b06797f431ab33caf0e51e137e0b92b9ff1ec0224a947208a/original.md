## `score` (Integrated)

```julia
score(S_Bkg, S_Obj, algorithm::Integrated)

score(S_Bkg, S_Obj, size, algorithm::Integrated)

score(S_Bkg, S_Obj, size, ρ, algorithm::Integrated)
```

Use the integrated intensity approach to find the total number of object voxels/volume/mass contained in `vol`.

The function can be called with different parameters:

1. `S_Bkg`, `S_Obj`, `algorithm` - Returns the total number of object voxels.
2. `S_Bkg`, `S_Obj`, `size`, `algorithm` - Returns the total object volume.
3. `S_Bkg`, `S_Obj`, `size`, `ρ`, `algorithm` - Returns the total object mass.

#### Inputs

  * `S_Bkg`: pure background signal intensity in the `vol`
  * `S_Obj`: pure object signal intensity in the `vol`
  * `size`: (optional) size of the voxels in the given `vol` (only for the 2nd and 3rd variations)
  * `ρ`: (optional) density of the given object of interest contained within the `vol` (only for the 3rd variation)
  * `algorithm`: the `Integrated` algorithm which accounts for noise and partial volume effect by integrating the intensity of the entire volume `vol`

#### References

[Integrated intensity-based technique for coronary artery calcium mass measurement: A phantom study](https://doi.org/10.1002/mp.16326)

[Accurate quantification of vessel cross-sectional area using CT angiography: a simulation study](https://doi.org/10.1007/s10554-016-1007-9)
