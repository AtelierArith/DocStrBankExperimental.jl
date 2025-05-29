`env = Env(ssp, layers, sspHS, z_krak, z_source; n_layers=2, note1="NVW", note2="A", bsig=0, z_step=1.0)`

Creates an underwater environment in the form of a sound speed profile (`ssp`), a half-space sound speed profile (`sspHS`), and a bottom profile (`bottom`).

The environment is used to compute the propagation of sound waves using Kraken.

Required arguments:

  * `ssp`: sound speed profile
  * `layers`: bottom profile
  * `sspHS`: half-space sound speed profile
  * `z_krak`: depth of receivers
  * `z_source`: depth of source

Optional keywords:

  * `n_layers`: number of layers in the environment (default: 2)
  * `note1`: note for the sound speed profile (default: "NVW")
  * `note2`: note for the half-space sound speed profile (default: "A")
  * `bsig`: bottom interfacial roughness (default: 0)
  * `n_sr`: number of sources (default: 1)
  * `z_sr`: depth of sources (default: 500)
  * `n_bc`: number of boundary conditions (default: size(ssp, 1))
