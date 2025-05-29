# VoronoiFVM.jl

[![Build status](https://github.com/j-fu/VoronoiFVM.jl/workflows/linux-macos-windows/badge.svg)](https://github.com/j-fu/VoronoiFVM.jl/actions) [![](https://img.shields.io/badge/docs-stable-blue.svg)](https://j-fu.github.io/VoronoiFVM.jl/stable) [![](https://img.shields.io/badge/docs-dev-blue.svg)](https://j-fu.github.io/VoronoiFVM.jl/dev) [![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.3529808.svg)](https://doi.org/10.5281/zenodo.3529808)

Solver for coupled nonlinear partial differential equations (elliptic-parabolic conservation laws) based on the Voronoi finite volume method. It uses automatic differentiation via [ForwardDiff.jl](https://github.com/JuliaDiff/ForwardDiff.jl) and [DiffResults.jl](https://github.com/JuliaDiff/DiffResults.jl) to evaluate user functions along with their jacobians and calculate derivatives of solutions with respect to their parameters.

## Accompanying packages

  * [VoronoiFVMDiffEq.jl](https://github.com/j-fu/VoronoiFVMDiffEq.jl): Glue package for using VoronoiFVM with DifferentialEquations.jl
  * [ExtendableSparse.jl](https://github.com/j-fu/ExtendableSparse.jl): convenient and efficient sparse matrix assembly
  * [ExtendableGrids.jl](https://github.com/j-fu/ExtendableGrids.jl): unstructured grid management library
  * [SimplexGridFactory.jl](https://github.com/j-fu/SimplexGridFactory.jl): unified high level  mesh generator interface
  * [Triangulate.jl](https://github.com/JuliaGeometry/Triangulate.jl):  Julia wrapper for the [Triangle](https://www.cs.cmu.edu/~quake/triangle.html) triangle mesh generator by J. Shewchuk
  * [TetGen.jl](https://github.com/JuliaGeometry/TetGen.jl):  Julia wrapper for the [TetGen](http://www.tetgen.org) tetrahedral mesh generator by H. Si.
  * [GridVisualize.jl](https://github.com/j-fu/GridVisualize.jl): grid and function visualization related to ExtendableGrids.jl
  * [PlutoVista.jl](https://github.com/j-fu/PlutoVista.jl): backend for [GridVisualize.jl](https://github.com/j-fu/GridVisualize.jl) for use in Pluto notebooks.

## Some alternatives

  * [GradientRobustMultiPhysics.jl](https://github.com/chmerdon/GradientRobustMultiPhysics.jl): finite element library implementing gradient robust FEM from the same package base by Ch. Merdon
  * [Trixi.jl](https://github.com/trixi-framework/Trixi.jl):  numerical simulation framework for hyperbolic conservation laws
  * [GridAP.jl](https://github.com/gridap/Gridap.jl) Grid-based approximation of partial differential equations in Julia
  * [Ferrite.jl](https://github.com/Ferrite-FEM/Ferrite.jl) Finite element toolbox for Julia
  * [FinEtools.jl](https://github.com/PetrKryslUCSD/FinEtools.jl)  Finite element tools for Julia

## [Changes](https://j-fu.github.io/VoronoiFVM.jl/stable/changes)

If you use this package in your work, please cite it according to [CITATION.bib](https://raw.githubusercontent.com/j-fu/VoronoiFVM.jl/master/CITATION.bib)

  * [`ContinuousQuantity`](@ref)
  * [`DiscontinuousQuantity`](@ref)
  * [`InterfaceQuantity`](@ref)
  * [`NewtonControl`](@ref)
  * [`NewtonSolverHistory`](@ref)
  * [`SolverControl`](@ref)
  * [`TestFunctionFactory`](@ref)
  * [`TransientSolution`](@ref)
  * [`TransientSolverHistory`](@ref)
  * [`bfacevelocities`](@ref)
  * [`boundary_dirichlet!`](@ref)
  * [`boundary_neumann!`](@ref)
  * [`boundary_robin!`](@ref)
  * [`cartesian!`](@ref)
  * [`check_allocs!`](@ref)
  * [`circular_symmetric!`](@ref)
  * [`coordinates`](@ref)
  * [`data`](@ref)
  * [`details`](@ref)
  * [`dof`](@ref)
  * [`edgelength`](@ref)
  * [`edgevelocities`](@ref)
  * [`embed!`](@ref)
  * [`embedparam`](@ref)
  * [`enable_boundary_species!`](@ref)
  * [`enable_discontinuous_species!`](@ref)
  * [`enable_species!`](@ref)
  * [`eval_jacobian!`](@ref)
  * [`eval_rhs!`](@ref)
  * [`evaluate_residual_and_jacobian`](@ref)
  * [`evolve!`](@ref)
  * [`fbernoulli`](@ref)
  * [`fbernoulli_pm`](@ref)
  * [`fixed_timesteps!`](@ref)
  * [`freqdomain_impedance`](@ref)
  * [`getdof`](@ref)
  * [`history`](@ref)
  * [`history_details`](@ref)
  * [`history_summary`](@ref)
  * [`impedance`](@ref)
  * [`integrate`](@ref)
  * [`mass_matrix`](@ref)
  * [`meas`](@ref)
  * [`measurement_derivative`](@ref)
  * [`nodeflux`](@ref)
  * [`num_dof`](@ref)
  * [`parameters`](@ref)
  * [`physics!`](@ref)
  * [`prepare_diffeq!`](@ref)
  * [`project`](@ref)
  * [`ramp`](@ref)
  * [`region`](@ref)
  * [`setdof!`](@ref)
  * [`solve`](@ref)
  * [`solve!`](@ref)
  * [`spherical_symmetric!`](@ref)
  * [`subgrids`](@ref)
  * [`testfunction`](@ref)
  * [`time`](@ref)
  * [`transient_solution`](@ref)
  * [`unknown_indices`](@ref)
  * [`unknowns`](@ref)
  * [`update_grid!`](@ref)
  * [`value`](@ref)
  * [`viewK`](@ref)
  * [`viewL`](@ref)
  * [`views`](@ref)
