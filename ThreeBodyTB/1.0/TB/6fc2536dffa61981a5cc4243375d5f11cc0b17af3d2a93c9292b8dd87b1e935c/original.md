function Hk(h::tb*crys*kspace, kpoint)

Calculate band structure at a k-point from a `tb_crys_kspace` object. Note, can only return precalculated k-points. Need real-space version to get arbitrary k-points.

#Returns

  * `vect` - Eigenvectors num*wan × num*wan complex matrix at kpoint
  * `vals` - Eigenvalues (num_wan)
  * `hk` - Hamiltonian at kpoint
  * `sk` - Overlap matrix at kpoint
  * `vals0` - <vect | Hk0 | vect> where Hk0 is the non-scf part of the Hamiltonian.

#Arguments

  * `h::tb_crys_kspace` - tb*crys*kspace object
  * `kpoint` - e.g. `[0.0,0.0,0.0]`
  * `scf=missing` - default is to take SCF from h.
