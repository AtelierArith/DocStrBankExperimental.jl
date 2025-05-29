mutable struct tb*crys*kspace{T}

k点タイトバインディングと結晶構造を保持します。`tb_crys`に似ています。

# 保持するもの

  * `tb::tb_k`
  * `crys::crystal`
  * `nelec::Float64`
  * `nspin::Int64`
  * `dftenergy::Float64`
  * `scf::Bool`
  * `gamma::Array{T, 2}`
  * `eden::Array{Float64,2}`
