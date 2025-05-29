Data type for a morphism of VarSet{T}s. Note we can equivalently view these  as morphisms [n]+T -> [m]+T fixing T or as morphisms [n] -> [m]+T, in the typical Kleisli category yoga. 

Currently, domains are treated as VarSets. The codom field is treated as a FinSet{Int}. Note that the codom accessor gives a VarSet while the codom field is just that VarSet's  FinSet of AttrVars. This could be generalized to being FinSet{Symbol} to allow for symbolic attributes. (Likewise, AttrVars will have to wrap Any rather than Int)
