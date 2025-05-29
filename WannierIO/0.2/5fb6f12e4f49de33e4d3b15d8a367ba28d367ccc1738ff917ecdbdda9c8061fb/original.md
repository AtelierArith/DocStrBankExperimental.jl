```julia
read_wout(filename; iterations)

```

Parse wannier90 `wout` file.

# Keyword Arguments

  * `iterations`: if `true`, parse all the iterations of disentanglement and   maximal localization. Default is `false`.

# Return

  * `lattice`: each column is a lattice vector in Å
  * `recip_lattice`: each column is a reciprocal lattice vector in Å⁻¹
  * `atom_labels`: atomic symbols
  * `atom_positions`: in fractional coordinates
  * `kgrid`: kpoint grid used in Wannierization
  * `centers`: center of each final WF, in Å
  * `spreads`: spread of each final WF, in Å²
  * `sum_centers`: sum of final WF centers, in Å
  * `sum_spreads`: sum of final WF spreads, in Å²
  * `ΩI`, `ΩD`, `ΩOD`, `Ωtotal`: final spread (components) in Å²
  * `phase_factors`: optional, global (multiplicative) phase factor for obtaining   real-valued (or close to real) MLWFs
  * `im_re_ratios`: optional, maximum Im/Re ratio
  * `iterations`: disentanglement and max localization convergence history,   only parsed when kwarg `iterations=true`
