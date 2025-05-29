Import unitary from an .npz file and create a LocalUnitaryMeasurementSetting object.

# Arguments:

  * `filepath::String`: Path to the input .npz file.
  * `site_indices::Union{Vector{Index{Int64}}, Nothing}`: Optional site indices. If not provided, they will be generated.

# Returns:

  * A LocalUnitaryMeasurementSettings object.
