```
sim!(plant::SimModel, N::Int, u=plant.uop.+1, d=plant.dop; x_0=plant.xop) -> res
```

Open-loop simulation of `plant` for `N` time steps, default to unit bump test on all inputs.

The manipulated inputs $\mathbf{u}$ and measured disturbances $\mathbf{d}$ are held constant at `u` and `d` values, respectively. The plant initial state $\mathbf{x}(0)$ is specified by `x_0` keyword arguments. The function returns [`SimResult`](@ref) instances  that can be visualized by calling `plot` on them. Note that the method mutates `plant` internal states.

# Examples

```jldoctest
julia> plant = NonLinModel((x,u,d,_)->0.1x+u+d, (x,_,_)->2x, 5, 1, 1, 1, 1, solver=nothing);

julia> res = sim!(plant, 15, [0], [0], x_0=[1])
Simulation results of NonLinModel with 15 time steps.
```
