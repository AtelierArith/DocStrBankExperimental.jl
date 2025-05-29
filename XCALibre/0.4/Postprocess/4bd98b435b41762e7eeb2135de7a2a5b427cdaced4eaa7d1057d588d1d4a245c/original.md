```
function boundary_average(patch::Symbol, field, config; time=0)
    # Extract mesh object
    mesh = field.mesh

    # Determine ID (index) of the boundary patch 
    ID = boundary_index(mesh.boundaries, patch)
    @info "calculating average on patch: $patch at index $ID"
    boundary = mesh.boundaries[ID]
    (; IDs_range) = boundary

    # Create face field of same type provided by user (scalar or vector)
    sum = nothing
    if typeof(field) <: VectorField 
        faceField = FaceVectorField(mesh)
        sum = zeros(_get_float(mesh), 3) # create zero vector
    else
        faceField = FaceScalarField(mesh)
        sum = zero(_get_float(mesh)) # create zero
    end

    # Interpolate CFD results to boundary
    interpolate!(faceField, field, config)
    correct_boundaries!(faceField, field, field.BCs, time, config)

    # Calculate the average
    for fID ∈ IDs_range
        sum += faceField[fID]
    end
    ave = sum/length(IDs_range)

    # return average
    return ave
end
```
