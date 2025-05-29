A Sweeps objects holds information about the various parameters controlling a density matrix renormalization group (DMRG) or similar matrix product state (MPS) calculation.

For a Sweeps object `sw` the available parameters are:

  * `nsweep(sw)` – the number of sweeps to do
  * `maxdim(sw,n)` – maximum MPS bond dimension for sweep n
  * `mindim(sw,n)` – minimum MPS bond dimension for sweep n
  * `cutoff(sw,n)` – truncation error cutoff for sweep n
  * `noise(sw,n)` – noise term coefficient for sweep n
