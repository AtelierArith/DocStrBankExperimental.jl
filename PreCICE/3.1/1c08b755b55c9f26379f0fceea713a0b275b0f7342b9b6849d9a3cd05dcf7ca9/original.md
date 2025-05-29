```
setMeshAccessRegion(meshName::String, boundingBox::AbstractArray{Float64})
```

This function is required if you don't want to use the mapping schemes in preCICE, but rather want to use your own solver for data mapping. As opposed to the usual preCICE mapping, only a single mesh (from the other participant) is now involved in this situation since an 'own' mesh defined by the participant itself is not required any more. In order to re-partition the received mesh, the participant needs to define the mesh region it wants read data from and write data to. The mesh region is specified through an axis-aligned bounding box given by the lower and upper [min and max] bounding-box limits in each space dimension [x, y, z].

# Arguments

  * `meshName::String`: Name of the mesh to define the access region for.
  * `boundingBox::AbstractArray{Float64}`: Axis-aligned bounding box. Example for 3D the format: [x*min, x*max, y*min, y*max, z*min, z*max]

# Notes

Defining a bounding box for serial runs of the solver (not to be confused with serial coupling mode) is valid. However, a warning is raised in case vertices are filtered out completely on the receiving side, since the associated data values of the filtered vertices are filled with zero data. This function can only be called once per participant and rank and trying to call it more than once results in an error. If you combine the direct access with a mapping (say you want to read data from a defined mesh, as usual, but you want to directly access and write data on a received mesh without a mapping) you may not need this function at all since the region of interest is already defined through the defined mesh used for data reading. This is the case if you define any mapping involving the directly accessed mesh on the receiving participant. (In parallel, only the cases read-consistent and write-conservative are relevant, as usual). The safety factor scaling (see safety-factor in the configuration file) is not applied to the defined access region and a specified safety will be ignored in case there is no additional mapping involved. However, in case a mapping is in addition to the direct access involved, you will receive (and gain access to) vertices inside the defined access region plus vertices inside the safety factor region resulting from the mapping. The default value of the safety factor is 0.5, i.e. the defined access region as computed through the involved provided mesh is by 50% enlarged.
