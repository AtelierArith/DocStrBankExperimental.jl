```julia
mutable struct ElectrolyteData{Tγ, Tcache, Texp, Tlog, Tflux} <: LiquidElectrolytes.AbstractElectrolyteData
```

Data for electrolyte. It is defined using [`Base.@kwdef`](https://docs.julialang.org/en/v1/base/base/#Base.@kwdef) allowing for keyword constructors like

```julia
    ElectrolyteData(nc=3,z=[-1,2,1])
```

The struct has three groups of fields:

  * Problem parameters: these are meant to be set by user in order to provide simulation parameters.
  * Derived values: these are derived from problem parameters by default, or via [`update_derived!`](@ref) after setting some of the problems pararmeters
  * Fixed values: these are mostly physical constants and values derived from them, they should not be changed.
  * Reserved fields: they are used to pass information during simulations and should not be set by the user.

Fields (reserved fields are modified by some algorithms):

  * `nc::Int64`: Number of charged species $N$.
  * `na::Int64`: Number of surface species
  * `iϕ::Int64`: Index of electrostatic potential $ϕ$ in species list.
  * `ip::Int64`: Index of pressure `p` in species list
  * `D::Vector{Float64}`: Mobility coefficients $D_i\; (i=1…N)$
  * `z::Vector{Int64}`: Charge numbers of ions $z_i\; (i=1…N)$
  * `M0::Float64`: Molar weight of solvent $M_0$
  * `M::Vector{Float64}`: Molar weights of ions $M_i\; (i=1…N)$
  * `v0::Float64`: Molar volume of solvent $v_0$
  * `v::Vector{Float64}`: Molar volumes of ions $v_i\; (i=1…N)$
  * `κ::Vector{Float64}`: Solvation numbers of ions $κ_i\; (i=1…N)$
  * `actcoeff!::Any`:     actcoeff!(γ, c, p, ::ElectrolyteData)

    Activity coefficient function. Write activity coefficients  $γ_i\; (i=1…N)$ into vector `γ`. Default: [`DGML_gamma!`](@ref).

  * `c_bulk::Vector{Float64}`: Bulk ion concentrations $c_i^b\; (i=1…N)$
  * `Γ_we::Int64`: Working electrode boundary number
  * `Γ_bulk::Int64`: Bulk boundary number
  * `ϕ_bulk::Float64`: Bulk voltage $ϕ^b$
  * `p_bulk::Float64`: Bulk pressure $p^b$
  * `T::Float64`: Temperature $T$
  * `ε::Float64`: Dielectric permittivity of solvent $ε$
  * `rexp::Any`: Regularized exponential, default: `exp` (unregularized)
  * `rlog::Any`: Regularized logarithm, default: `log` (unregularized)
  * `pscale::Float64`: Pressure scaling factor. Default: 1.0e9
  * `eneutral::Bool`: Local electroneutrality switch. Default: false
  * `upwindflux!::Any`: Upwind flux caculation method for ionic species. This allows to choose between

      * [`μex_flux!`](@ref) (default, strongly preferrable): excess chemical potential (SEDAN) scheme
      * [`act_flux!`](@ref): scheme based on reciprocal activity coefficients
      * [`cent_flux!`](@ref): central scheme

  * `weights::Vector{Float64}`: Species weights for norms in solver control.

  * `solvepressure::Bool`: Solve for pressure.

    This is `true` by default. Setting this to `false` can serve two purposes:

      * Use the pressure from the solution of a flow equation
      * Ignore the pressure contribution to the excess chemical potential

  * `F::Float64`: Faraday constant $F$ (fixed)
  * `ε_0::Float64`: Dielectric permittivity of vacuum $ε_0$ (fixed)
  * `RT::Float64`: Molar gas constant scaled with temperature $RT$ (derived)
  * `Mrel::Vector{Float64}`: Solvated molar mass ratio $m_i = \frac{M_i}{M_0} + κ_i \; (i=1… N)$ (derived)
  * `vrel::Vector{Float64}`: Solvated molar volume ratio $\hat v_i =  \frac{v_i}{v_0} + κ_i \; (i=1… N)$ (derived)
  * `barv::Vector{Float64}`: Solvated molar volume $\bar v_i = v_i + κ_i v_0 \; (i=1… N)$ (derived)
  * `tildev::Vector{Float64}`: Pressure relevant volume $\tilde v_i = \bar v_i + m_i v_0 \; (i=1… N)$  (derived)
  * `γ_bulk::Vector{Float64}`: Activity coefficients at bulk interface $γ_i^b= γ_i(c_1^b … c_N^b, p^b) \; (i=1… N)$ (derived)
  * `γk_cache::Any`: Cache for activity coefficient calculation (reserved)
  * `γl_cache::Any`: Cache for activity coefficient calculation (reserved)
  * `ϕ_we::Float64`: Working electrode voltage $ϕ_{we}$ (reserved) Used by sweep algorithms to pass boundary data.

  * `edgevelocity::Union{Float64, Vector{Float64}}`: Edge velocity projection (reserved).

  * `scheme::Symbol`: Scheme parameter. Deprecated and disabled. Use `upwindflux!` instead to change the discretization scheme.
