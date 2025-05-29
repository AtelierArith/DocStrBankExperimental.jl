mutable struct tb*crys*kspace{T}

Hold k-point tight binding and crystal structure. Similar to `tb_crys`

# Holds

  * `tb::tb_k`
  * `crys::crystal`
  * `nelec::Float64`
  * `nspin::Int64`
  * `dftenergy::Float64`
  * `scf::Bool`
  * `gamma::Array{T, 2}`
  * `eden::Array{Float64,2}`
