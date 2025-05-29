```julia
abstract type PsPFile
```

Abstract type representing a pseudopotential file.

The structure of the data should closely mirror the format of the file, and the values of quantities should be exactly those found in the file.

Required methods:

```julia
# A unique string, usually a hash or checksum.
function identifier(file::PsPFile)::AbstractString end
# A short string listing the file format (e.g. `"PSP8"`)
function format(file::PsPFile)::AbstractString end
# The symbol of the element for which the file contains a pseudopotential (e.g. `"Ag"`)
function elemental_symbol(file::PsPFile)::AbstractString end
# The maximum angular momentum channel contained in the file
function max_angular_momentum(file::PsPFile)::Integer end
# The number of non-local projectors for angular momentum `l` contained in the file
function n_projector_radials(file::PsPFile, l::Integer)::Integer end
# The number of chi functions for angular momentum `l` contained in the file
function n_chi_function_radials(file::PsPFile, l::Integer)::Integer end
# The pseudo-atomic valence charge
function valence_charge(file::PsPFile)::Real end
# Whether the file contains a norm-conserving pseudopotential
function is_norm_conserving(file::PsPFile)::Bool end
# Whether the file contains an ultrasoft pseudopotential
function is_ultrasoft(file::PsPFile)::Bool end
# Whether the file contains a projector-augmented wave pseudopotential
function is_paw(file::PsPFile)::Bool end
# Whether the file contains a pseudopotential supporting spin-orbit coupled calculations
function has_spin_orbit(file::PsPFile)::Bool end
# Whether the file contains a pseudopotential supporting non-linear core corrections
function has_core_density(file::PsPFile)::Bool end
```
