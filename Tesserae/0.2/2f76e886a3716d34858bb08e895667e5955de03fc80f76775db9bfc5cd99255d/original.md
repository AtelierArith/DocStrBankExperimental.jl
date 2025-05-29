```
generate_particles([ParticleProp], mesh; alg=PoissonDiskSampling())
```

Generate particles across the entire `mesh` domain based on the selected `alg` algorithm. See also [`GridSampling`](@ref) and [`PoissonDiskSampling`](@ref).

The generated `particles` is a [`StructArray`](https://github.com/JuliaArrays/StructArrays.jl) where each element is of type `ParticleProp`. The first field of `ParticleProp` is designated for particle positions.

```jldoctest
julia> ParticleProp = @NamedTuple begin
           x  :: Vec{2, Float64}
           m  :: Float64
           V  :: Float64
           v  :: Vec{2, Float64}
           F  :: SecondOrderTensor{2, Float64, 4}
           σ  :: SymmetricSecondOrderTensor{2, Float64, 3}
       end
@NamedTuple{x::Vec{2, Float64}, m::Float64, V::Float64, v::Vec{2, Float64}, F::Tensor{Tuple{2, 2}, Float64, 2, 4}, σ::SymmetricSecondOrderTensor{2, Float64, 3}}

julia> mesh = CartesianMesh(0.5, (0,3), (0,2));

julia> particles = generate_particles(ParticleProp, mesh; alg=GridSampling());

julia> particles.F[1] = one(eltype(particles.F));

julia> particles[1]
(x = [0.125, 0.125], m = 0.0, V = 0.0, v = [0.0, 0.0], F = [1.0 0.0; 0.0 1.0], σ = [0.0 0.0; 0.0 0.0])

julia> particles.F
96-element Vector{Tensor{Tuple{2, 2}, Float64, 2, 4}}:
 [1.0 0.0; 0.0 1.0]
 [0.0 0.0; 0.0 0.0]
 [0.0 0.0; 0.0 0.0]
 [0.0 0.0; 0.0 0.0]
 [0.0 0.0; 0.0 0.0]
 [0.0 0.0; 0.0 0.0]
 [0.0 0.0; 0.0 0.0]
 [0.0 0.0; 0.0 0.0]
 [0.0 0.0; 0.0 0.0]
 [0.0 0.0; 0.0 0.0]
 ⋮
 [0.0 0.0; 0.0 0.0]
 [0.0 0.0; 0.0 0.0]
 [0.0 0.0; 0.0 0.0]
 [0.0 0.0; 0.0 0.0]
 [0.0 0.0; 0.0 0.0]
 [0.0 0.0; 0.0 0.0]
 [0.0 0.0; 0.0 0.0]
 [0.0 0.0; 0.0 0.0]
 [0.0 0.0; 0.0 0.0]
```
