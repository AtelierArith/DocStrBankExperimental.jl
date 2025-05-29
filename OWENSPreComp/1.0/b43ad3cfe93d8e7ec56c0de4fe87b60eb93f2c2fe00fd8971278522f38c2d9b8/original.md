```
properties(chord::Array{<:Real,1}, tw_aero_d::Array{<:Real,1},
tw_prime_d::Array{<:Real,1}, le_loc::Real, xnode::Array{<:Real,1},
ynode::Array{<:Real,1}, e1::Array{<:Real,1}, e2::Array{<:Real,1},
g12::Array{<:Real,1}, anu12::Array{<:Real,1}, density::Array{<:Real,1},
xsec_nodeU::Array{<:Real,1}, n_laminaU::Array{Int64,1},
n_pliesU::Array{Int64,1}, t_lamU::Array{<:Real,1},
tht_lamU::Array{<:Real,1}, mat_lamU::Array{Int64,1},
xsec_nodeL::Array{<:Real,1}, n_laminaL::Array{Int64,1},
n_pliesL::Array{Int64,1}, t_lamL::Array{<:Real,1},
tht_lamL::Array{<:Real,1}, mat_lamL::Array{Int64,1},
loc_web::Array{<:Real,1}, n_laminaW::Array{Int64,1},
n_pliesW::Array{Int64,1}, t_lamW::Array{<:Real,1},
tht_lamW::Array{<:Real,1}, mat_lamW::Array{Int64,1})
```

Calculates span-variant structural properties for composite blades

# Inputs

  * `chord::Real`: section chord length (m)
  * `tw_aero_d::Real`: section twist angle (deg)
  * `tw_prime_d::Real`: derivative of section twist angle w.r.t. span location (deg/m)
  * `le_loc::Real`: leading edge location relative to reference axis (normalized by chord)
  * `xnode::Array{<:Real,1}`: x airfoil coordinates starting at leading edge traversing upper surface and back around lower surface
  * `ynode::Array{<:Real,1}`: y airfoil coordinates starting at leading edge traversing upper surface and back around lower surface
  * `e1::Array{<:Real,1}`: E1
  * `e2::Array{<:Real,1}`: E2
  * `g12::Array{<:Real,1}`: G12
  * `anu12::Array{<:Real,1}`: Nu12
  * `density::Array{<:Real,1}`: density
  * `xsec_nodeU::Array{<:Real,1}`: upper surface normalized chord location of sector boundaries
  * `n_laminaU::Array{Int64,1}`: upper surface number of lamina in each sector
  * `n_pliesU::Array{Int64,1}`: upper surface number of plies
  * `t_lamU::Array{<:Real,1}`: upper surface ply thickness (m) for the lamina
  * `tht_lamU::Array{<:Real,1}`: upper surface orientation (deg) for the lamina
  * `mat_lamU::Array{Int64,1}`: upper surface material id for the lamina
  * `xsec_nodeL::Array{<:Real,1}`: lower surface normalized chord location of sector boundaries
  * `n_laminaL::Array{Int64,1}`: lower surface number of lamina in each sector
  * `n_pliesL::Array{Int64,1}`: lower surface number of plies
  * `t_lamL::Array{<:Real,1}`: lower surface ply thickness (m) for the lamina
  * `tht_lamL::Array{<:Real,1}`: lower surface orientation (deg) for the lamina
  * `mat_lamL::Array{Int64,1}`: lower surface material id for the lamina
  * `loc_web::Array{<:Real,1}`: web normalized chord location of sector boundaries
  * `n_laminaW::Array{Int64,1}`: web number of lamina in each sector
  * `n_pliesW::Array{Int64,1}`: web number of plies
  * `t_lamW::Array{<:Real,1}`: web ply thickness (m) for the lamina
  * `tht_lamW::Array{<:Real,1}`: web orientation (deg) for the lamina
  * `mat_lamW::Array{Int64,1}`: web material id for the lamina

# Outputs:

  * `eifbar`: ei_flap, Section flap bending stiffness about the YE axis (Nm2)
  * `eilbar`: ei_lag, Section lag (edgewise) bending stiffness about the XE axis (Nm2)
  * `gjbar`: gj, Section torsion stiffness (Nm2)
  * `eabar`: ea, Section axial stiffness (N)
  * `eiflbar`: s_fl, Coupled flap-lag stiffness with respect to the XE-YE frame (Nm2)
  * `sfbar`: s_af, Coupled axial-flap stiffness with respect to the XE-YE frame (Nm)
  * `slbar`: s_al, Coupled axial-lag stiffness with respect to the XE-YE frame (Nm.)
  * `sftbar`: s_ft, Coupled flap-torsion stiffness with respect to the XE-YE frame (Nm2)
  * `sltbar`: s_lt, Coupled lag-torsion stiffness with respect to the XE-YE frame (Nm2)
  * `satbar`: s_at, Coupled axial-torsion stiffness (Nm)
  * `z_sc`: x_sc, X-coordinate of the shear-center offset with respect to the XR-YR axes (m)
  * `y_sc`: y_sc, Chordwise offset of the section shear-center with respect to the reference frame, XR-YR (m)
  * `ztc_ref`: x_tc, X-coordinate of the tension-center offset with respect to the XR-YR axes (m)
  * `ytc_ref`: y_tc, Chordwise offset of the section tension-center with respect to the XR-YR axes (m)
  * `mass`: mass, Section mass per unit length (Kg/m)
  * `iflap_eta`: flap_iner, Section flap inertia about the YG axis per unit length (Kg-m)
  * `ilag_zeta`: lag_iner, Section lag inertia about the XG axis per unit length (Kg-m)
  * `tw_iner_d`: tw*iner*d, Orientation of the section principal inertia axes with respect the blade reference plane, θ (deg)
  * `zcm_ref`: x_cm, X-coordinate of the center-of-mass offset with respect to the XR-YR axes (m)
  * `ycm_ref`: y_cm, Chordwise offset of the section center of mass with respect to the XR-YR axes (m)
  * `n_af_nodes`: number of airfoil nodes
  * `n_materials`: number of materials
  * `n_sctU`: number of sectors on upper
  * `n_sctL`: number of sectors on lower
  * `nwebin`: number of webs
  * `n_laminaTotalU`: total number of lamina on upper
  * `n_laminaTotalL`: total number of lamina on lower
  * `n_laminaTotalW`: total number of lamina on webs
