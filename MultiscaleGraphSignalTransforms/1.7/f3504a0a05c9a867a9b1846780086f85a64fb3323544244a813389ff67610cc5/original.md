getall*expansioncoeffs2(G*Sig::GraphSig, GP*star::GraphPart,                                  GP*star*Lsym::GraphPart,                                  VM*NGWP::Array{Float64,3},                                  PC*NGWP::Array{Float64,3},                                  LP*NGWP::Array{Float64,3},                                  VM*NGWP*Lsym::Array{Float64,3},                                  PC*NGWP*Lsym::Array{Float64,3},                                  LP*NGWP*Lsym::Array{Float64,3},                                  𝚽::Matrix{Float64},                                  𝚽sym::Matrix{Float64})

get all expansion coefficients of `f` in dissertation via all methods in NGWP.jl and MTSG.jl

# Input Arguments

  * `G_Sig::GraphSig`: GraphSig of the primal graph
  * `GP_star::GraphPart`: GraphPart of the dual graph
  * `VM_NGWP::Array{Float64,3}`: varimax NGWP.
  * `PC_NGWP::Array{Float64,3}`: pair-clustering NGWP.
  * `LP_NGWP::Array{Float64,3}`: lapped NGWP.
  * `VM_NGWP_Lsym::Array{Float64,3}`: Lsym version of varimax NGWP.
  * `PC_NGWP_Lsym::Array{Float64,3}`: Lsym version of pair-clustering NGWP.
  * `LP_NGWP_Lsym::Array{Float64,3}`: Lsym version of lapped NGWP.
  * `𝚽::Matrix{Float64}`: the matrix of `L` eigenvectors.
  * `𝚽sym::Matrix{Float64}`: the matrix of `Lsym` eigenvectors.
