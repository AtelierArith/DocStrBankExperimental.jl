```
Environment
```

The Environment struct is required for most methods and defines the geometrical setup, constants, and stores the relevant data together. The microphone array is assumed to be at the center of the coordinate system. The fields are

# Arguments

*Required:*

  * `micgeom::Array{T,2}`: (x,y,z) coordinates for microhone array.
  * `z0::Real`: distance to source plane from microphone array.
  * `CSM::FreqArray`: Cross-spectral matrix, size `M x M x Nf`, where `M` is the number of microphones and `Nf` is the number of frequency bins.

*Optional:*

  * `flim::Tuple=extrema(CSM.fc)`: Frequency limits (fmin,fmax).
  * `Nx::Integer=21`: Number of computational gridpoint in x direction.
  * `Ny::Integer=21`: Number of computational gridpoint in y direction.
  * `xlim::Tuple=(-1.,1.)`: Cartesian x-coordinate limits.
  * `ylim::Tuple=(-1.,1.)`: Cartesian y-coordinate limits.
  * `wv=ones(size(micgeom,2))`: Microphones on/off.
  * `wc::Bool=false`: Microphones coherence weighting.
  * `dr::Bool=false`: Diagonal removal of CSM
  * `w=ones(M,Nf)`: Microphone weights. If `wc=true` it calculates coherence weighting.
  * `shear::Bool = false`: Amiet phase correction
  * `ampcorr::Bool = shear`: Amiet amplitude correction (only applies when shear = true)
  * `c::Real=343.`: Speed of sound [m/s].
  * `Ma::Real=0.0`: Mach number (sign determines flow direction)
  * `h::Real=0.0`: Distance from array center to shear layer (Amiet correction) should be supplied when `Ma != 0`.
  * `multi_thread::Bool = false`: Enable multi-threading via the ThreadsX package.
