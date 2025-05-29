## `Integrated`

```julia
function Integrated(
    vol, 
    I=sum(vol), 
    N=length(vol)
)
```

#### Inputs

  * vol: region of interest
  * I: integrated intensity of the entire `vol`
  * N: total number of voxels contained in the entire `vol`

#### References

[Integrated intensity-based technique for coronary artery calcium mass measurement: A phantom study](https://doi.org/10.1002/mp.16326)

[Accurate quantification of vessel cross-sectional area using CT angiography: a simulation study](https://doi.org/10.1007/s10554-016-1007-9)
