This module `Murphy.jl` has been ported in december 2020 from

murphy.g Copyright (C) July 1998  Andrew Mathas     mathas@maths.usyd.edu.au University of Sydney

It allows computations with the Murphy basis of an Hecke algebra of type A.

Multiplication  of Murphy basis elements is  done using the Garnir tableaux as  described in Murphy's paper [Mur1995](biblio.htm#Mur95). This also lets us convert from the T-basis to the Murphy basis since     `T_w = M([[1],…,[n]], [[1],…,[n]]) * T_w`. (We use "M" for the Murphy basis).

As with the T-basis, Murphy basis elements are implemented by `ModuleElts`. Here the keys are standard tableaux pairs. These are represented by a tuple `(mu,s,t)` where `mu`, `s` and `t` are all integers and `H.Murphy.partitions[mu]` is the associated partition and `H.Murphy.tableaux[mu][s]` (resp `t`) is a named tuple describing `s` (this tuple is described in the function `initMurphy()` below).

Throughout memory considerations are thrown to the wind as we cache many of the  more horrible expansions as we go along  in order to save time when we next need them.
