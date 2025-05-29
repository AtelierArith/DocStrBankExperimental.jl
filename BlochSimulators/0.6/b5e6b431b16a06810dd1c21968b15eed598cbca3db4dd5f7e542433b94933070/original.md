```
magnetization_to_signal(::Union{CPU1,CPUThreads,CUDALibs}, magnetization, parameters, trajectory::CartesianTrajectory2D, coordinates, coil_sensitivities)
```

# Arguments

  * `magnetization`:          Matrix{Complex} of size (# readouts, # voxels) with phase-encoded                   magnetization at echo times.
  * `parameters`:     Tissue parameters of all voxels, including spatial coordinates.
  * `trajectory`:     Cartesian trajectory struct.
  * `coordinates`:    Vector{Coordinates} with spatial coordinates for each voxel.
  * `coil_sensitivities`:     Matrix{Complex} of size (# voxels, # coils) with coil sensitivities.

# Returns

  * `signal`: Vector of length (# coils) with each element a Matrix{Complex}       of size (# readouts, # samples per readout)

# Extended help

As noted in the description of the simulate_signal function (see `src/simulate/signal.jl`), we simulate the MR signal at timepoint `t` from coil `i` as: signalᵢ[t] = sum(m[t,v] * cᵢ[v] * ρ[v]  for v in 1:(# voxels)), where `cᵢ`is the coil sensitivity profile of coil `i`, `ρ` is the proton density map and `m` the matrix with the magnetization at all timepoints for each voxel obtained through Bloch simulations.

The output (signalᵢ) for each coil is in principle a `Vector{Complex}``of length (# samples per readout) * (# readouts). If we reshape the output into a`Matrix{Complex}`of size (# samples per readout, # readouts) instead, and do something similar for`m`, then the signal value associated with the s-th sample point of the r-th readout can be expressed as signalᵢ[r,s] = sum( m[r,s,v]] * cᵢ[v] * ρ[v]  for v in 1:(# voxels)).

The problem here is that we typically cannot store the full m. Instead, we compute the magnetization at echo times only. The reason is that, if mᵣ is the magnetization at the r-th echo time in some voxel, and E = exp(-Δt*R₂[v]) * exp(im*(Δkₓ*x[v])) is the change per sample point (WHICH FOR CARTESIAN SEQUENCES IS THE SAME FOR ALL READOUTS AND SAMPLES), then the magnetization at the s-th sample relative the the echo time can can be computed as mₛ = mᵣ * E[v]^s

Therefore we can write

signalⱼ[r,s] = sum( magnetization[r,v] * E[v]^s * ρ[v] * cⱼ[v] for v in 1:(# voxels)) signalⱼ[r,s] = magnetization[r,:] * (E.^s .* ρ .* cⱼ)

Because the (E.^s .* ρ .* cⱼ)-part is the same for all readouts, we can simply perform this computation for all readouts simultaneously as signalⱼ[:,s] = magnetization * (E.^s .* ρ .* cⱼ)

If we define the matrix Eˢ as E .^ (-(ns÷2):(ns÷2)-1), then we can do the computation for all different sample points at the same time as well using a single matrix-matrix multiplication: signalⱼ = magnetization * (Eˢ .* (ρ .* cⱼ))

The signalⱼ array is of size (# readouts, # samples per readout). We prefer to have it transposed, therefore we compute signalⱼ = transpose(Eˢ .* (ρ .* cⱼ)) * transpose(magnetization) instead.

For the final output, we do this calculation for each coil j and get a vector of signal matrices (one matrix for each coil) as a result.

Note that this implementation relies entirely on vectorized code and works on both CPU and GPU. The matrix-matrix multiplications are - I think - already multi-threaded so a separate multi-threaded implementation is not needed.
