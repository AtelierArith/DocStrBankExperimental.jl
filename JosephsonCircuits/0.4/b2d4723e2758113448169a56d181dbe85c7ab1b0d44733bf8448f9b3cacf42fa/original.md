```
hbsolve(ws, wp::NTuple{N,Number}, sources::Vector,
    Nmodulationharmonics::NTuple{M,Int}, Npumpharmonics::NTuple{N,Int},
    circuit, circuitdefs;dc = false, threewavemixing = false,
    fourwavemixing = true, maxintermodorder=Inf, iterations = 1000,
    ftol = 1e-8, switchofflinesearchtol = 1e-5, alphamin = 1e-4,
    symfreqvar = nothing, nbatches = Base.Threads.nthreads(),
    sorting = :number, returnS = true, returnSnoise = false, returnQE = true,
    returnCM = true, returnnodeflux = false, returnvoltage = false,
    returnnodefluxadjoint = false, returnvoltageadjoint = false,
    keyedarrays::Val{K} = Val(true), sensitivitynames::Vector{String} = String[],
    returnSsensitivity = false, returnZ = false, returnZadjoint = false,
    returnZsensitivity = false, returnZsensitivityadjoint = false,
    factorization = KLUfactorization()) where {N,M,K}
```

Calls the harmonic balance solvers, [`hbnlsolve`](@ref) and [`hblinsolve`](@ref), which work for an arbitrary number of modes and ports, and for both three and four wave mixing processes. See also [`hbnlsolve`](@ref) and [`hblinsolve`](@ref).

# Arguments

  * `ws`: the angular frequency or frequencies of the signal in Hz such as   2*pi*5.0e9 or 2*pi*(4.5:0.001:5.0)*1e9.
  * `wp::NTuple{N,Number}`: a tuple containing the angular frequencies of the   strong tones (or pumps) such as (2*pi*5.0e9,) for a single pump at 5 GHz   (2*pi*5.0e9,2*pi*6.0e9) for a pump at 5 GHz and a pump at 6 GHz. The   frequencies should be non-commensurate. For commensurate pumps, the lowest   pump frequency should be provided here, and the other pumps added to   `sources` with a mode index equal to the ratio.
  * `sources::Vector`: a vector of named tuples specifying the mode index,   port, and current for each source. The named tuple(s) have names   mode, port, and current. mode is a tuple specifying the mode or harmonic   indices of the pumps, port is an integer specifying the port, and current   is a number specifying the current. Note that the current is a complex   number    For example:   [(mode=(1,0),port=1,current=Ip1),(mode=(0,1),port=1,current=Ip2)]   specifies two pumps where the frequency of the first pump would be   1*wp1 + 0*wp2 and the second 0*wp1+1*wp2 where wp1 is the first   pump frequency and wp2 is the second pump frequency. Both of the pumps are   applied to port 1 with currents Ip1 and Ip2, respectively.
  * `Nmodulationharmonics::NTuple{M,Int}`: a tuple of integers describing how   many signal and idler modes.
  * `Npumpharmonics::NTuple{N,Int}`: a tuple of integers describing how many   harmonics to simulate for each of the pumps. The length of the tuple must   equal the number of non-commensurate pumps.
  * `circuit`: vector of tuples each of which contain the component name, the   first node, the second node, and the component value. The first three must   be strings.
  * `circuitdefs`: a dictionary where the keys are symbols or symbolic   variables for component values and the values are the numerical values   for the components.

# Keywords

  * `dc = false`: include 0 frequency terms in the harmonic balance analysis.
  * `threewavemixing = false`: simulate three wave mixing processes.
  * `fourwavemixing = true`: simulate four wave mixing processes.
  * `maxintermodorder=Inf`: the maximum intermod order as defined by the sum of   the absolute values of the integers multiplying each of the frequencies   being less than or equal to `maxintermodorder`. This performs a diamond   truncation of the discrete Fourier space.
  * `iterations = 1000`: the number of iterations before the nonlinear solver   returns an error.
  * `ftol = 1e-8`: the function tolerance defined we considered converged,   defined as norm(F)/norm(x) < ftol or norm(F,Inf) <= ftol.
  * `switchofflinesearchtol = 1e-5`: the function tolerance at which we switch   from Newton with linesearch to only Newton. For easily converging   functions, setting this to zero can speed up simulations.
  * `alphamin = 1e-4`: the minimum step size relative to 1 for the linesearch.
  * `symfreqvar = nothing`: the symbolic frequency variable, eg `w`.
  * `nbatches = Base.Threads.nthreads()`: the number of batches to split the   signal frequencies into for multi-threading. Set to 1 for singled threaded   evaluation.
  * `sorting = :number`: sort the nodes by:   `:name`: Sort the vector of strings. This always works but leads   to results like "101" comes before "11".   `:number`: Convert the node strings to integer and sort by these   (this errors if the nodes names cannot be converted to integers).   `:none`: Don't perform any sorting except to place the ground node   first. In other words, order the nodes in the order they are found in   `circuit`.
  * `returnS = true`: return the scattering parameters from the linearized   simulations.
  * `returnSnoise = false`: return the noise scattering parameters from the   linearized simulations.
  * `returnQE = true`: return the quantum efficiency from the linearized   simulations.
  * `returnCM = true`: return the commutation relations from the linearized   simulations.
  * `returnnodeflux = false`: return the node fluxes from the linearized   simulations.
  * `returnvoltage = false`: return the node voltages from the linearized   simulations.
  * `returnnodefluxadjoint = false`: return the node fluxes from the linearized   adjoint simulations.
  * `returnvoltageadjoint = false`: return the node voltages from the linearized   adjoint simulations.
  * `keyedarrays::Val{K} = Val(true)`: when Val(true) return the output matrices   and vectors as keyed arrays for more intuitive indexing. When Val(false)   return normal matrices and vectors.
  * `sensitivitynames::Vector{String} = String[]`: the component names for which   to return the sensitivities (in progress).
  * `returnSsensitivity = false`: return the scattering parameter sensitivity   matrix from the linearized simulations (in progress).
  * `returnZ = false`: return the impedance matrix from the linearized   simulations.
  * `returnZadjoint = false`: return the impedance matrix from the linearized   adjoint simulations.
  * `returnZsensitivity = false`: return the Z parameter sensitivity   matrix from the linearized simulations (in progress).
  * `returnZsensitivityadjoint = false`: return the Z parameter sensitivity   matrix from the linearized adjoint simulations (in progress).
  * `factorization = KLUfactorization()`: the type of factorization to use for   the nonlinear and the linearized simulations.

# Returns

  * `HB`: A simple structure to hold the harmonic balance solutions. See   [`HB`](@ref).
