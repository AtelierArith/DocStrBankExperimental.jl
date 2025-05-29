Inplace Gottesman canonicalization of a tableau.

This uses different canonical form from [`canonicalize!`](@ref). It is used in the computation of the logical X and Z operators of a [`MixedDestabilizer`](@ref).

It returns the (in place) modified state, the indices of the last pivot of both Gaussian elimination steps, and the permutations that have been used to put the X and Z tableaux in standard form.

Based on [gottesman1997stabilizer](@cite).

See also: [`canonicalize!`](@ref), [`canonicalize_rref!`](@ref)
