```
create_sim(mesh; args...)
```

Create a micromagnetic simulation instance with given arguments. 

  * `mesh`: a mesh has to be provided to start the simulation. The mesh could be [`FDMesh`](@ref), [`CubicMesh`](@ref), or [`TriangularMesh`](@ref).

# Arguments

  * `name` : the simulation name, should be a string.
  * `driver` : the driver name, should be a string. By default, the driver is "SD".
  * `alpha` : the Gilbert damping in the LLG equation, should be a number.
  * `beta` : the nonadiabatic strength in the LLG equation with spin transfer torques (zhang-li model), should be a number.
  * `gamma` : the gyromagnetic ratio, default value = 2.21e5.
  * `ux`, `uy` or `uz`: the strengths of the spin transfer torque.
  * `ufun` : the time-dependent function for `u`.
  * `Ms`: the saturation magnetization, should be [`NumberOrArrayOrFunction`](@ref). By default, Ms=8e5
  * `mu_s`: the magnetic moment, should be [`NumberOrArrayOrFunction`](@ref). By default, mu*s=2*mu*B
  * `A` or `J`: the exchange constant, should be [`NumberOrArrayOrFunction`](@ref).
  * `D` : the DMI constant, should be [`NumberOrArrayOrFunction`](@ref).
  * `dmi_type` : the type of DMI, could be "bulk", "interfacial" or "D2d".
  * `Ku`: the anisotropy constant, should be [`NumberOrArrayOrFunction`](@ref).
  * `axis`: the anisotropy axis, should be a tuple, such as (0,0, 1)
  * `Kc`: the cubic anisotropy constant, should be [`NumberOrArrayOrFunction`](@ref).
  * `axis1`: the cubic anisotropy axis1, should be a tuple, such as (1,0,0)
  * `axis2`: the cubic anisotropy axis2, should be a tuple, such as (0,1,0)
  * `demag` : include demagnetization or not, should be a boolean, i.e., true or false. By default,  demag=false.
  * `H`: the external field, should be a tuple or function, i.e., [`TupleOrArrayOrFunction`](@ref).
  * `m0` : the initial magnetization, should be a tuple or function, i.e., [`TupleOrArrayOrFunction`](@ref).
  * `T` : the temperature, should be should be [`NumberOrArrayOrFunction`](@ref).
  * `shape` : the shape defines the geometry of the sample, where parameters are configured.
