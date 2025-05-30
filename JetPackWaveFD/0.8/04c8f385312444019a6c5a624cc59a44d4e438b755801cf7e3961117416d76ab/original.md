```
JopNlProp2DAcoIsoDenQ_DEO2_FDTD(; kwargs...)
JopLnProp2DAcoIsoDenQ_DEO2_FDTD(; v, kwargs...)
```

Create a `Jets` nonlinear or linearized operator for 2D visco-acoustic, isotropic,  variable density modeling.

# Model Parameters

This propagator operates with two model parameters, as shown in the table below.

| Parameter | Description                   |
|:---------:|:----------------------------- |
|    `v`    | P wave velocity               |
|    `b`    | buoyancy (reciprocal density) |

Velocity `v` and buoyancy `b` can be **active** parameters and inverted for using the Jacobian machinery, or **passive** parameters that are constant. If a parameter is **active** there will be a component of model assigned to it.

The model is 3D with the slowest dimension for model parameter.  The earth model property maps to the slow- dimension array index via the `state(F).active_modelset` dictionary.

# Examples

## Model and acquisition geometry setup

1. load modules Jets, WaveFD, and JetPackWaveFD
2. set up the model discretization, coordinate size and spacing
3. set up the acquisition geometry, including the time discretization, locations for source and receivers, and the source wavelet
4. create constant buoyancy array

```
using Jets, WaveFD, JetPackWaveFD
nz,nx = 200, 100                      # spatial discretization size
dz,dx = 20.0, 20.0                    # spatial discretization sampling
ntrec = 1101                          # number of temporal samples in recorded data
dtrec = 0.0100                        # sample rate for recorded data
dtmod = 0.0025                        # sample rate for modeled data
wavelet = WaveletCausalRicker(f=5.0)  # type of wavelet to use (source signature) 
sz = dz                               # source Z location 
sx = dx*(nx/2)                        # source X location 
rx = dx*[0:0.5:nx-1;];                # array of receiver X locations
rz = 2*dz*ones(length(0:0.5:nx-1));   # array of receiver Z locations
b = ones(Float32, nz, nx);            # buoyancy model (reciprocal density)
```

## Construct and apply the nonlinear operator

1. create the nonlinear operator `F`
2. create the constant velocity model m₀
3. perform nonlinear forward modeling with constant velocity model `m₀` and return the resulting modeled data in `d`

```
F = JopNlProp2DAcoIsoDenQ_DEO2_FDTD(; b = b, ntrec = ntrec, 
    dz = dz, dx = dx, dtrec = dtrec, dtmod = dtmod, wavelet = wavelet, 
    sz = sz, sx = sx, rz = rz, rx = rx)
m₀ = 1500 .* ones(domain(F));
d = F*m₀;              # forward nonlinear op
```

## Construct and apply the linearized Jacobian operator (method 1)

1. create the nonlinear operator `F` directly by construction of a jet.
2. create the constant velocity model m₀
3. create the Jacobian operator `J` by linearization of `F` at point `m₀`
4. create a random model perturbation vector `δm`.
5. perform linearized forward (Born) modeling on the model perturbation vector `δm` and   return the resulting data perturbation in `δd`.
6. perform linearized adjoint (Born) migration on the data perturbation vector `δd` and   return the resulting model perturbation in `δm`.

Note that the Jacobian operators `J` and `J'` require the serialized nonlinear forward wavefield,  and this is generated automatically whenever required. If you watch the logging to standard out from this example, you will first see the finite difference evolution for the nonlinear forward,  followed by the linearized forward, and finally the linearized adjoint.

```
F = JopNlProp2DAcoIsoDenQ_DEO2_FDTD(; b = b, ntrec = ntrec, 
    dz = dz, dx = dx, dtrec = dtrec, dtmod = dtmod, wavelet = wavelet, 
    sz = sz, sx = sx, rz = rz, rx = rx)
m₀ = 1500 .* ones(domain(F));
J = jacobian(F, m₀)
δm = rand(domain(J));
δd = J*δm;             # forward linearized op
δm = J'*δd;            # adjoint linearized op
```

## Construct and apply the linearized Jacobian operator (method 2)

1. create the constant velocity model m₀
2. create the Jacobian operator `J` at point `m₀` directly by construction of a jet.
3. create a random model perturbation vector `δm`.
4. perform linearized forward (Born) modeling on the model perturbation vector `δm` and   return the resulting data perturbation in `δd`.
5. perform linearized adjoint (Born) migration on the data perturbation vector `δd` and   return the resulting model perturbation in `δm`.

```
m₀ = 1500 * ones(Float32, nz, nx);
J = JopLnProp2DAcoIsoDenQ_DEO2_FDTD(; v = m₀, b = b, ntrec = ntrec, 
    dz = dz, dx = dx, dtrec = dtrec, dtmod = dtmod, wavelet = wavelet, 
    sz = sz, sx = sx, rz = rz, rx = rx)
δm = rand(domain(J));
δd = J*δm;             # forward linearized op
δm = J'*δd;            # adjoint linearized op
```

# Required Parameters

  * `v` the point at which the jet is linearized. Note this argument is required in the constuctor for     `JopLnProp2DAcoIsoDenQ_DEO2_FDTD` but not `JopNlProp2DAcoIsoDenQ_DEO2_FDTD`. This constuctor is shown     in the last example above.
  * `dtmod` The sample rate for the modeled data. You can establish a lower bound for the modeling sample rate     with the following expression: `dt = 0.75 * 0.38 * max(dx,dz) / maximum(v)`. Note that the usual     Courant–Friedrichs–Lewy condition (CFL condition) for stability in finite difference modeling is     modified *heuristically* to include the impact of the visco-acoustic implementation of this operator,     requiring a 25% smaller smaple rate.
  * `dtrec` The number of time samples in the recorded data. Note requirement that `dtrec`    be an even multiple of `dtmod`.
  * `ntrec` The number of time samples in the recorded data. Note that the number of samples in the modeled     data is determined from `ntrec`, `dtrec`, and `dtmod`.

# Optional Parameters

Defaults for arguments are shown inside square brackets.

  * `b [ones(Float32,0,0)]` the buoyancy (reciprocal density) array.
  * `srcfieldfile [joinpath(tempdir(), "field-fd6eb01f-62c1-4bcb-bbde-c4925110739a.bin")]` the full path to a scratch file used for    the serializationof the compressed nonlinear source wavefield.
  * `comptype [nothing]` the type of compression to use for the serialization of   the nonlinear source wavefield. The type of compression must be one of:

      * `nothing` - no compression.
      * `Float32` - if wavefield is `Float64`, then do a simple conversion to Float32.
      * `UInt32` - compression using CvxCompress (windowing + 2D wavelet transform +    thresholding + quantization + run-length-encoding).
  * `compscale [1e-2]` determines the thresholding for the compression of the nonlinear source    wavefield prior to serialization. Larger values mean more aggressive compression. You can    likely increase compscale to 1.0 before you start to notice differences in output from    Jacobian operations.
  * `nz_subcube, nx_subcube [32]` The Z and X sizes of windows used for compression    of the nonlinear source wavefield with `CvxCompress`. Note the requirement   `[8 <= n*_subcube <=256]`.
  * `isinterior [false]` boolean flag that indicates how the nonlinear source wavefield is   saved. For large models, operation will be faster with `isinterior = true`, but    the linearization correctness test may fail.

      * `true` the entire model including absorbing boundaries is serialized and deserialized
      * `false` the interior part of the model excluding absorbing boundaries is serialized    and deserialized
  * `sz [0.0]` Array of source Z coordinate. Note that if multiple sources are provided,    they will will be injected simultaneously during finite difference evolution.
  * `sx [0.0]` Array of source X coordinate.
  * `st [0.0]` Array of source delay times.
  * `interpmethod [:hicks]` Type of physical interpolation for sources and receivers. For locations    that are not on the physical grid coordinates, interpolation is used either to inject or extract   information. `interpmethod` must be one of:

      * `:hicks` Hicks 2D sinc interpolation (up to 8x8 nonzero points per location)
      * `:linear` bilinear interpolation (up to 2x2 nonzero points per location)
  * `rz [[0.0]]` 2D array of receiver Z coordinates
  * `rx [[0.0]]` 2D array of receiver Z coordinates
  * `z0 [0.0]` Origin of physical coordinates for the Z dimension.
  * `x0 [0.0]` Origin of physical coordinates for the X dimension.
  * `dz [10.0]` Spacing of physical coordinates in the Z dimension.
  * `dx [10.0]` Spacing of physical coordinates in the X dimension.
  * `freqQ [5.0]` The center frequency for the Maxwell body approximation to dissipation only attenuation.   Please see `JetPackWaveFD` package documentation for more information concerning the attenuation model.
  * `qMin [0.1]` The minimum value for Qp at the boundary of the model used in our Maxwell body approximation   to dissipation only attenuation. This is not a physically meaningful value for Qp, as we use the    attenuation to implement absorbing boundary conditions and eliminate outgoing waves on the    boundaries of the computational domain.    Please see `JetPackWaveFD` package documentation for more information concerning the attenuation model.
  * `qInterior [100.0]` the value for Qp in the interior of the model used in our Maxwell body approximation   to dissipation only attenuation. This is the value for Qp away from the absorbing boundaries and is    a physically meaningful value.   Please see `JetPackWaveFD` package documentation for more information concerning the attenuation model.
  * `padz, padx [0.0], [0.0]` - apply extra padding to the survey determined aperture in `Ginsu`.   Please see `Ginsu` for more information.
  * `nbz_cache, nbx_cache [512], [8]` The size of cache blocks in the Z and X dimensions.    In general the cache block in the Z (fast) dimension should be ≥ the entire size of that dimension,    and the cache block size in the slower dimension is generally small in order to allow the entire   block to fit in cache.
  * `nsponge [50]` The number of grid cells to use for the absorbing boundary. For high fidelity modeling   this should be > 60 grid points, but can be significantly smaller for some use cases like low frequency    full waveform inversion.
  * `wavelet [WaveletCausalRicker(f=5.0)]` The source wavelet, can be specified as either a Wavelet type    or an array.
  * `freesurface [false]` Determines if a free surface (`true`) or absorbing (`false`) top boundary condition   is applied.
  * `imgcondition` ["standard"] Selects the type of imaging condition used. Choose from "standard", "FWI",    and "RTM". "FWI" and "RTM" will perform Kz wavenumber filtering prior to the imaging condition   in order to promote long wavelengths (for FWI), or remove long wavelength backscattered energy (for    RTM).  "MIX" mixes the FWI imaging condition using the parameter RTM_weight. Note the true adjoint    only exists for "standard" imaging condition currently.
  * `RTM_weight [0.5]` determines the balance of short wavelengths and long wavelengths in the imaging condition.    A value of 0.0 is equivalent to the FWI imaging condition, a value of 0.5 is equivalent to the standard   imaging condtion, and a value of 1.0 is equivalent to the RTM imaging condition.
  * `nthreads [Sys.CPU_THREADS]` The number of threads to use for OpenMP parallelization of the modeling.
  * `reportinterval [500]` The interval at which information about the propagtion is logged.

See also: `Ginsu`, `WaveletSine`, `WaveletRicker`, `WaveletMinPhaseRicker`, `WaveletDerivRicker`,     `WaveletCausalRicker`, `WaveletOrmsby`, `WaveletMinPhaseOrmsby` 
