```
get3DData(eq::BloodFlowEquations2D,semi,sol,time_index ::Int = 1;vtk ::Bool=false,out ::T="./datas") where {T<:AbstractString,F1<:Function,F2<:Function,F3<:Function}
```

Generates 3D spatial data from a 2D blood flow model for visualization. This will use a straight vessel. This function extracts unique node coordinates, computes relevant flow parameters, and generates a 3D representation of the arterial domain using cylindrical coordinates. Optionally, it can export the data in VTK format.

### Parameters

  * `eq::BloodFlowEquations1D`: Instance of `BloodFlowEquations1D` representing the blood flow model.
  * `semi`: Semi-discretization structure containing mesh and numerical information.
  * `sol`: Solution array containing the numerical state variables.
  * `time_index::Int=1`: Time step index for extracting the solution (default: 1).
  * `vtk::Bool=false`: Whether to export data to VTK format (default: `false`).
  * `out::T="./datas"`: Output directory for VTK files (default: `"./datas"`).

### Returns

Named tuple containing:

  * `x`: X-coordinates of the generated 3D points.
  * `y`: Y-coordinates of the generated 3D points.
  * `z`: Z-coordinates of the generated 3D points.
  * `A`: Cross-sectional areas at each point.
  * `wtheta`: Flow angular velocity at each point.
  * `ws`: Flow axial velocity at each point.
