```
struct FESpace{Tv, Ti, FEType<:AbstractFiniteElement,AT<:AssemblyType}
	name::String                          # full name of finite element space (used in messages)
	broken::Bool                          # if true, broken dofmaps are generated
	ndofs::Int                            # total number of dofs
	coffset::Int                          # offset for component dofs
	xgrid::ExtendableGrid[Tv,Ti}          # link to xgrid 
	dofgrid::ExtendableGrid{Tv,Ti}	      # link to (sub) grid used for dof numbering (expected to be equal to or child grid of xgrid)
	dofmaps::Dict{Type{<:AbstractGridComponent},Any} # backpack with dofmaps
    interpolators::Dict{Type{<:AssemblyType}, Any} # backpack with interpolators
end
```

A struct that has a finite element type as parameter and carries dofmaps (CellDofs, FaceDofs, BFaceDofs) plus additional grid information and access to arrays holding coefficients if needed.
