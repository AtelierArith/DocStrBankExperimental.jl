```
Scenario
```

Scenarios to simulate: `instances(Scenario)`

  * `F_CAVI = 1` –> lid-driven cavity
  * `F_COUE = 2` –> Couette flow
  * `F_POIS = 3` –> Hagen–Poiseuille flow
  * `F_PULL = 4` –> tether pulling from a flat patch
  * `F_BEND = 5` –> bending of a flat patch

The first letter indicates mesh [`Topology`](@ref): `F` for a flat patch and `C` for a cylinder. At present, no cylindrical scenarios are implemented.

To create a new scenario:

  * add and export a new entry in the `Scenario` enum
  * edit [`get_scenario_bc_info`](@ref) in `src/input/Bc.jl`
  * write the corresponding `apply_<SCENARIO>_bcs` function in `src/input/Mesh.jl`
  * add the new `scenario` to the `implemented` list in `src/input/Params.jl`
