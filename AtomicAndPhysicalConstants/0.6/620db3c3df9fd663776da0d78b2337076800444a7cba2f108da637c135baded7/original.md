SubatomicSpecies 

## Description:

> mutable struct to store all (possibly degenerate) information about a subatomic particle<


## Fields:

  * `species_name`      – String common name for (anti) baryon
  * `charge`            – electric charge on the given particle in units of [e+]
  * `mass`              – mass of the given particle in [eV/c^2]
  * `moment`  							– magnetic moment of particle in [eV/T]
  * `spin`              – spin of the particle in [ħ]

## Notes:

some parameters in this struct are likely named constants from PhysicalConstants.jl

## Examples:

  * `SubatomicSpecies("neutron", 0, m_neutron, anom_mag_moment_neutron, 0.5)`
  * `SubatomicSpecies("pion-", -1, m_pion_charged, 0.0, 0.0)`
