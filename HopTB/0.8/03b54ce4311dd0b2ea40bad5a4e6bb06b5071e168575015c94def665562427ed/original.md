`TBModel{T<Number}` is a data type representing tight binding models.

# Fields

  * `norbits::Int64`: number of orbits in the model
  * `lat::SMatrix{3,3,Float64,9}`: primitive lattice vectors stored in columns
  * `rlat::SMatrix{3,3,Float64,9}`: primitive reciprocal lattice vectors stored in columns
  * `hoppings::Dict{SVector{3,Int16},Matrix{T}}`: R -> ⟨0n|H|Rm⟩, where n is the first index and m is the second index.
  * `overlaps::Dict{SVector{3,Int16},Matrix{T}}`: R -> ⟨0n|Rm⟩
  * `positions::Dict{SVector{3,Int16},SVector{3,Matrix{T}}}`: R -> [⟨0n|rx|Rm⟩, ⟨0n|ry|Rm⟩, ⟨0n|rz|Rm⟩]
  * `isorthogonal`: whether the different orbitals of the model is orthogonal to each other.
  * `nsites::Union{Missing,Int16}`: It is possible that the orbitals can be grouped into several sites. Every group of orbitals should share the same position within the group, stored in `site_positions`.
  * `site_norbits::Union{Missing,Vector{Int64}}`: number of orbitals for each site.
  * `site_positions::Union{Missing,Matrix{Float64}}`: position of sites stored in column
  * `orbital_types::Union{Missing,Vector{Vector{Int16}}}`: It is possible that the orbitals have definite symmetry representations. Example: `orbital_types = [[0], [0, 1]]` denotes that there are two sites, the first of which has 1 s orbital and the second of which has 1 s orbital and 1 p orbital (4 orbitals in total not counting spin). The orbitals of the TBModel should appear in a consistent order denoted by `orbital_types`.
  * `isspinful::Union{Missing,Bool}`: If a TBModel is spinful, the first half of the orbitals should be spin up and the second half should be spin down. The two halves of the orbitals should be in one-to-one correspondence.
  * `is_canonical_ordered::Union{Missing,Bool}`: If the orbital types are know, and `is_canonical_ordered` is true, then the orbitals are guaranteed to appear in a canonical order defined by decreasing Lz value. For example, canonical order of p orbitals should -px-i*py, pz, px-i*py. See the wikipedia for other orbitals.

# Missing data

Not all fields of TBModels are required to have a valid value. For example, it is possible the site information is missing for some models. Here are some rules:

  * `nsites`, `site_norbits`, `site_positions` should all either be missing or valid.
  * `orbital_types` can only be valid if `nsites`, `site_norbits` and `site_positions` are valid.
  * `is_canonical_ordered` can only be valid if `orbital_types` is valid.

# Consistency check

Any functions that directly modifies a TBModel should always maintain the following consistencies (if relevant fields are not missing):

  * `hoppings`, `overlaps` and `positions` matrices should always be Hermitian.
  * `overlap[[0, 0, 0]]` should always be positive definite.
  * `diag(position[[0, 0, 0]][α])/diag(overlap[[0, 0, 0]])` should be consistent with `site_positions`.
  * number of orbits should be consistent.
