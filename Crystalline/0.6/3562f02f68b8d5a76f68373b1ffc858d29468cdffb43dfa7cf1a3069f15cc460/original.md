```
ENANTIOMORPHIC_PAIRS :: NTuple{11, Pair{Int,Int}}
```

Return the space group numbers of the 11 enantiomorphic space group pairs in 3D.

The space group types associated with each such pair `(sgnum, sgnum')` are related by a mirror transformation: i.e. there exists a transformation  $\mathbb{P} = \{\mathbf{P}|\mathbf{p}\}$ between the two groups $G = \{g\}$ and $G' = \{g'\}$ such that $G' = \mathbb{P}^{-1}G\mathbb{P}$ where $\mathbf{P}$ is improper (i.e. $\mathrm{det}\mathbf{P} < 0$).

We define distinct space group *types* as those that cannot be related by a proper transformation (i.e. with $\mathrm{det}\mathbf{P} > 0$). With that view, there are 230 space group types. If the condition is relaxed to allow improper rotations, there are  $230-11 = 219$ distinct *affine* space group types. See e.g. ITA5 Section 8.2.2.

The enantiomorphic space group types are also chiral space group types in 3D. There are no enantiomorphic pairs in lower dimensions; in 3D all enantiomorphic pairs involve screw symmetries, whose direction is inverted between pairs (i.e. have opposite handedness).
