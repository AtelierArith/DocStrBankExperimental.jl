Compute the Maximimum Common C-Sets from a vector of C-Sets.

Find an ACSet `$a$ with maximum possible size ($|a|$) such that there is a   monic span of ACSets $a₁ ← a → a₂$. There may be many maps from this overlap  into each of the inputs, so a Vector{Vector{ACSetTransformations}} per overlap  is returned (a cartesian product can be taken of these to obtain all possible  multispans for that overlap). If there are multiple overlaps of equal size,  these are all returned.

If there are attributes, we ignore these and use variables in the apex of the  overlap.
