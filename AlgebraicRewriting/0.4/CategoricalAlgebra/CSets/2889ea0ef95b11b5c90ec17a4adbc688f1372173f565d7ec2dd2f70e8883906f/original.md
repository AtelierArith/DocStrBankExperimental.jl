Compute pushout complement of attributed C-sets, if possible.

The pushout complement is constructed pointwise from pushout complements of finite sets. If any of the pointwise identification conditions fail (in FinSet), this method will raise an error. If the dangling condition fails, the resulting C-set will be only partially defined. To check all these conditions in advance, use the function [`can_pushout_complement`](@ref).
