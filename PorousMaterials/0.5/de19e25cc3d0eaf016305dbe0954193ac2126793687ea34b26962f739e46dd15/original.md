Data structure for a molecule/adsorbate.

# Attributes

  * `species::Symbol`: Species of molecule, e.g. `:CO2`
  * `atoms::Atoms`: array of Lennard-Jones spheres comprising the molecule
  * `charges::Charges`: array of point charges comprising the molecule
  * `com::Coords`: center of mass
