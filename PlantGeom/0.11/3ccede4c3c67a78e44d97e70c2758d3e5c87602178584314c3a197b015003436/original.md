```
read_ops(file; attr_type=Dict{String,Any}, mtg_type=MutableNodeMTG)
```

Reads an OPS file and returns the content as a `MultiScaleTreeGraph`.

# Arguments

  * `file::String`: Path of the `.ops` file to read.
  * `attr_type::Type=Dict{Symbol,Any}`: Type of the attributes to use.
  * `mtg_type::Type`: Type of the MTG to use, e.g. `NodeMTG` or `MutableNodeMTG`.

# Returns

A `MultiScaleTreeGraph` of the scene, with the OPFs as children of the scene node. The dimension of the scene is available in the `scene_dimensions` attribute of the scene node. Each root node of the OPFs has a `scene_transformation` attribute that stores the transformation applied to the OPF by the scene. It allows updating the scene transformations and write the scene back to disk. The OPF root node also has the following attributes:

  * `sceneID::Int`: Scene ID.
  * `plantID::Int`: Plant ID.
  * `filePath::String`: Path to the original `.opf` file.
  * `pos::Meshes.Point`: Position of the object.
  * `scale::Float64`: Scale of the object.
  * `inclinationAzimut::Float64`: Inclination azimut of the object.
  * `inclinationAngle::Float64`: Inclination angle of the object.
  * `rotation::Float64`: Rotation of the object.
  * `functional_group::String`: Functional group of the object.

# Details

Node IDs of the OPFs are recomputed at import to ensure their uniqueness in the larger scene MTG.

# Example

```julia
using CairoMakie, PlantGeom
joinpath(pathof(PlantGeom) |> dirname |> dirname, "test", "files", "scene.ops") |> read_ops |> viz
```
