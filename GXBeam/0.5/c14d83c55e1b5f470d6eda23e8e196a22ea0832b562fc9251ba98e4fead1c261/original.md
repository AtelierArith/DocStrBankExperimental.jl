```
strain_recovery(F, M, nodes, elements, cache; gxbeam_order=true)
```

Compute stresses and strains at each element in cross section.

# Arguments

  * `F::Vector(3)`: force at this cross section in x, y, z directions
  * `M::Vector(3)`: moment at this cross section in x, y, z directions
  * `nodes::Vector{Node{TF}}`: all the nodes in the mesh
  * `elements::Vector{MeshElement{TF}}`: all the elements in the mesh
  * `cache::SectionCache`: needs to reuse data from the compliance solve   (thus must initialize cache and pass it to both compliance and this function)

# Keyword Arguments

  * `gxbeam_order=true::Bool`: if true, `F``and`M`are assumed to be in the   local beam axis used by GXBeam (where the beam extends along the x-axis). This   also returns beam stresses and strains in the axis order set by GXBeam   (e.g. axial stresses would correspond to the`xx` direction, or first index).

# Returns

  * `strain_b::Vector(6, ne)`: strains in beam coordinate system for each element. order: xx, yy, zz, xy, xz, yz   Note: this order (as well as those below) corresponds to the local beam reference frame if `gxbeam_order`   is set to `true`.
  * `stress_b::Vector(6, ne)`: stresses in beam coordinate system for each element. order: xx, yy, zz, xy, xz, yz
  * `strain_p::Vector(6, ne)`: strains in ply coordinate system for each element. order: 11, 22, 33, 12, 13, 23
  * `stress_p::Vector(6, ne)`: stresses in ply coordinate system for each element. order: 11, 22, 33, 12, 13, 23
