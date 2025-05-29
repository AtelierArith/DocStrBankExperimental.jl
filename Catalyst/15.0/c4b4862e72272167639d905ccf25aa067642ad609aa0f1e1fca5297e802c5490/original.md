```julia
struct LatticeReactionSystem{Q, R, S, T} <: ModelingToolkit.AbstractTimeDependentSystem
```

A representation of a spatial system of chemical reactions on a discrete (lattice) space.

# Fields

  * `reactionsystem`: The (non-spatial) reaction system within each vertex.
  * `spatial_reactions`: The spatial reactions defined between individual vertices.
  * `lattice`: The lattice on which the (discrete) spatial system is defined.
  * `num_verts`: The number of vertices (compartments).
  * `num_edges`: The number of edges.
  * `num_species`: The number of species.
  * `spatial_species`: List of species that may move spatially.
  * `parameters`: All parameters related to the lattice reaction system (both those whose values are tied to vertices and edges).

  * `vertex_parameters`: Parameters which values are tied to vertices, e.g. that possibly could have unique values at each vertex of the system.

  * `edge_parameters`: Parameters whose values are tied to edges (adjacencies), e.g. that possibly could have unique values at each edge of the system.

  * `edge_iterator`: An iterator over all the lattice's edges. Currently, the format is always a Vector{Pair{Int64,Int64}}. However, in the future, different types could potentially be used for different types of lattice (E.g. for a Cartesian grid, we do not technically need to enumerate each edge)

Arguments:

  * `rs`: The non-spatial [`ReactionSystem`](@ref) model that is expanded to a spatial model.
  * `srs`: A vector of spatial reactions. These provide the rules for how species may move spatially.
  * `lattice`: Either a Cartesian grid, a masked grid, or a graph. This describes the discrete space

to which the non-spatial model is expanded.

Keyword Arguments:

  * `diagonal_connections = false`: Only relevant for Cartesian and masked lattices. If `true`,

diagonally adjacent compartments are considered adjacent, and spatial reactions in between these are possible.

Example:

```julia
# Fetch packages.
using Catalyst, OrdinaryDiffEqDefault
import CairoMakie

# Creates the `LatticeReactionSystem` model.
rs = @reaction_network begin
    (p,d), 0 <--> X
end
diffusion_rx = @transport_reaction D X
lattice = CartesianGrid((5,5))
lrs = LatticeReactionSystem(rs, [diffusion_rx], lattice)

# Simulates the model (using ODE and jumps).
u0 = [:X => rand(5,5)]
tspan = (0.0, 1.0)
ps = [:p => 1.0, :d => 0.5, :D => 0.1]
oprob = ODEProblem(lrs, u0, tspan, ps)
osol = solve(oprob)

# Saves an animation of the solution to the file "lattice_animation.mp4".
lattice_animation(osol, :X, lrs, "lattice_animation.mp4")
```

Notes:

  * Spatial modelling in Catalyst is still a work in progress, any feedback (or contributions) to this

is highly welcome.

  * `LatticeReactionSystem`s are primarily intended to model systems in discrete space. Modelling

continuous space systems with them is possible, but requires the user to determine the discretisation (the lattice). Better support for continuous space models is a work in progress.

  * Catalyst contains extensive documentation on spatial modelling, which can be found [here](https://docs.sciml.ai/Catalyst/stable/spatial_modelling/lattice_reaction_systems/).
