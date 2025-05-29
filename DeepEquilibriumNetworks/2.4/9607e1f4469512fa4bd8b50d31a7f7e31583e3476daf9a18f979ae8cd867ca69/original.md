```
MultiScaleDeepEquilibriumNetwork(main_layers::Tuple, mapping_layers::Matrix,
    post_fuse_layer::Union{Nothing, Tuple}, solver,
    scales::NTuple{N, NTuple{L, Int64}}; kwargs...)
```

Multi Scale Deep Equilibrium Network as proposed in [baimultiscale2020](@cite).

## Arguments

  * `main_layers`: Tuple of Neural Networks. Each Neural Network is applied to the corresponding scale.
  * `mapping_layers`: Matrix of Neural Networks. Each Neural Network is applied to the corresponding scale and the corresponding layer.
  * `post_fuse_layer`: Neural Network applied to the fused output of the main layers.
  * `solver`: Solver for the rootfinding problem. ODE Solvers and Nonlinear Solvers are both supported.
  * `scales`: Scales of the Multi Scale DEQ. Each scale is a tuple of integers. The length of the tuple is the number of layers in the corresponding main layer.

For keyword arguments, see [`DeepEquilibriumNetwork`](@ref).

## Example

```jldoctest
julia> main_layers = (
           Parallel(+, Dense(4 => 4, tanh; use_bias=false), Dense(4 => 4, tanh; use_bias=false)),
           Dense(3 => 3, tanh), Dense(2 => 2, tanh), Dense(1 => 1, tanh));

julia> mapping_layers = [NoOpLayer() Dense(4 => 3, tanh) Dense(4 => 2, tanh) Dense(4 => 1, tanh);
                         Dense(3 => 4, tanh) NoOpLayer() Dense(3 => 2, tanh) Dense(3 => 1, tanh);
                         Dense(2 => 4, tanh) Dense(2 => 3, tanh) NoOpLayer() Dense(2 => 1, tanh);
                         Dense(1 => 4, tanh) Dense(1 => 3, tanh) Dense(1 => 2, tanh) NoOpLayer()];

julia> model = MultiScaleDeepEquilibriumNetwork(
           main_layers, mapping_layers, nothing, NewtonRaphson(), ((4,), (3,), (2,), (1,)));

julia> rng = Xoshiro(0);

julia> ps, st = Lux.setup(rng, model);

julia> x = rand(rng, Float32, 4, 12);

julia> size.(first(model(x, ps, st)))
((4, 12), (3, 12), (2, 12), (1, 12))
```
