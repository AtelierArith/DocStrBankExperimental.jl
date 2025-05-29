```
CnoidalWaveSerreGreenNaghdi(param; P=1)
```

Compute the Serre-Green-Naghdi cnoidal wave with prescribed `h₀<h₁<h₂`. `h₁` is the minimum, `h₂` is the maximum of the wave. As `h₀ -> h₁`, the cnoidal wave converges towards the solitary wave. See for instance [Gavrilyuk, Nkonga, Shyue and Truskinovsky](https://doi.org/10.1088/1361-6544/ab95ac).

# Arguments

  * `param :: NamedTuple`: parameters of the problem containing `h₀<h₁<h₂` and dimensionless parameters `ϵ` and `μ`, and number of collocation points `N`.
  * `P :: Int`: (keyword, optional, default = 1) the number of periods of the cnoidal wave in the constructed mesh.

# Return values

`(η,u,v,mesh,param)` with

  * `η :: Vector{Float64}`: surface deformation;
  * `u :: Vector{Float64}`: layer-averaged velocity;
  * `v :: Vector{Float64}`: derivative of the trace of the velocity potential at the surface;
  * `mesh :: Mesh`: mesh collocation points;
  * `param :: NamedTuple`: useful parameters
