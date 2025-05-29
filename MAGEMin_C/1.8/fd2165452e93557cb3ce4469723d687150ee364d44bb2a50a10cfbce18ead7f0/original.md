Out*PT =multi*point*minimization(P::T2,T::T2,MAGEMin*db::MAGEMin*Data;test::Int64=0,X::Union{Nothing, AbstractVector{Float64}, AbstractVector{<:AbstractVector{Float64}}}=nothing,B::Union{Nothing, T1, Vector{T1}}=nothing,W::Union{Nothing, Vector{MAGEMin*C.W*data{Float64, Int64}}}=nothing,Xoxides=Vector{String},sys*in="mol",progressbar=true,                                  callback*fn ::Union{Nothing, Function}= nothing,                                   callback*int::Int64 = 1) where {T1 <: Float64, T2 <: AbstractVector{T1}}

Perform (parallel) MAGEMin calculations for a range of points as a function of pressure `P`, temperature `T` and/or composition `X`. The database `MAGEMin_db` must be initialised before calling the routine. The bulk-rock composition can either be set to be one of the pre-defined build-in test cases, or can be specified specifically by passing `X`, `Xoxides` and `sys_in` (that specifies whether the input is in "mol" or "wt").

Below a few examples:

# Example 1 - build-in test vs. pressure and temperature

```julia
julia> data = Initialize_MAGEMin("ig", verbose=false);
julia> n = 10
julia> P = rand(8:40.0,n)
julia> T = rand(800:1500.0,n)
julia> out = multi_point_minimization(P, T, data, test=0)
julia> Finalize_MAGEMin(data)
```

# Example 2 - Specify constant bulk rock composition for all points:

```julia
julia> data = Initialize_MAGEMin("ig", verbose=false);
julia> n = 10
julia> P = fill(10.0,n)
julia> T = fill(1100.0,n)
julia> Xoxides = ["SiO2"; "Al2O3"; "CaO"; "MgO"; "FeO"; "Fe2O3"; "K2O"; "Na2O"; "TiO2"; "Cr2O3"; "H2O"];
julia> X = [48.43; 15.19; 11.57; 10.13; 6.65; 1.64; 0.59; 1.87; 0.68; 0.0; 3.0];
julia> sys_in = "wt"
julia> out = multi_point_minimization(P, T, data, X=X, Xoxides=Xoxides, sys_in=sys_in)
julia> Finalize_MAGEMin(data)
```

# Example 3 - Different bulk rock composition for different points

```julia
julia> data = Initialize_MAGEMin("ig", verbose=false);
julia> P = [10.0, 20.0]
julia> T = [1100.0, 1200]
julia> Xoxides = ["SiO2"; "Al2O3"; "CaO"; "MgO"; "FeO"; "Fe2O3"; "K2O"; "Na2O"; "TiO2"; "Cr2O3"; "H2O"];
julia> X1 = [48.43; 15.19; 11.57; 10.13; 6.65; 1.64; 0.59; 1.87; 0.68; 0.0; 3.0];
julia> X2 = [49.43; 14.19; 11.57; 10.13; 6.65; 1.64; 0.59; 1.87; 0.68; 0.0; 3.0];
julia> X = [X1,X2]
julia> sys_in = "wt"
julia> out = multi_point_minimization(P, T, data, X=X, Xoxides=Xoxides, sys_in=sys_in)
julia> Finalize_MAGEMin(data)
```

# Activating multithreading on julia

To take advantage of multithreading, you need to start julia from the terminal with:

```bash
$ julia -t auto
```

which will automatically use all threads on your machine. Alternatively, use `julia -t 4` to start it on 4 threads. If you are interested to see what you can do on your machine type:

```
julia> versioninfo()
```
