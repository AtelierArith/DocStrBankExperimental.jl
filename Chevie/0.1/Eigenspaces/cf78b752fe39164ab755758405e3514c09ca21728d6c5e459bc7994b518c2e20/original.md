Eigenspaces and `d`-Harish-Chandra series

Let  `Wϕ` be a  reflection coset on  a vector space  `V`; that is `Φ∈GL(V)` normalizes  the reflection group  `W`. Let `Lwϕ`  be a reflection subcoset; that  is `L` is a  parabolic subgroup of `W`  (the fixator of a subspace of `V`)  and  `w∈  W`  is  such  that  `wΦ`  normalizes `L`. There are several interesting  cases where the *relative group* $N_W(Lwϕ)/L$, or a subgroup of it normalizing some further data attached to `L`, is itself a reflection group.

A first example is the case where `ϕ=1` and `w=1`, `W` is the Weyl group of a   finite  reductive   group  $𝐆^F$   and  the   Levi  subgroup  $𝐋^F$ corresponding  to `L` has a cuspidal unipotent character. Then $N_W(L)/L$ is  a  Coxeter  group  acting  on  the  space  `X(Z𝐋)⊗ℝ`.  A  combinatorial characterization of such parabolic subgroups of Coxeter groups is that they are  normalized by the  longest element of  larger parabolic subgroups (see [5.7.1 Lusztig1976](biblio.htm#Lus76)).

A  second  example  is  when  `L`  is  trivial  and  `wϕ` is a *`ζ`-regular element*,  that is  the `ζ`-eigenspace  $V_ζ$ of  `wϕ` contains  a vector outside  all the reflecting hyperplanes of `W`. Then $N_W(Lwϕ)/L=C_W(wϕ)$ is a reflection group in its action on $V_ζ$.

A similar but more general example is when $V_ζ$ is the `ζ`-eigenspace of some  element of  the reflection  coset `Wϕ`,  and is  of maximal dimension among  such `ζ`-eigenspaces. Then the set of  elements of `Wϕ` which act by `ζ`  on  $V_ζ$  is  a  certain  subcoset  `Lwϕ`,  and $N_W(Lwϕ)/L$ is a reflection group in its action on $V_ζ$ (see [2.5 Lehrer-Springer1999](biblio.htm#LS99)).

Finally,  a  still  more  general  example,  but which only occurs for Weyl groups  or  Spetsial  reflection  groups,  is  when `𝐋` is a `ζ`-split Levi subgroup  (which means that  the corresponding subcoset  `Lwϕ` is formed of all  the elements which act by `ζ` on  some subspace `V_ζ` of `V`), and `λ` is  a  `d`-cuspidal  unipotent  character  of  `𝐋`  (which  means  that the multiplicity  of `ζ`  as a  root of  the degree  of `λ`  is the same as the multiplicity  of `ζ` as a root of the generic order of the semi-simple part of  `𝐆`); then $N_W(Lwϕ,λ)/L$ is a complex reflection group in its action on `V_ζ`.

Further,  in the above cases the relative group describes the decomposition of a Lusztig induction.

When  $𝐆^F$ is  a finite  reductive group,  and `λ`  a cuspidal unipotent character  of  the  Levi  subgroup  $𝐋^F$,  then the $𝐆^F$-endomorphism algebra  of  the  Harish-Chandra  induced  representation $R_𝐋^𝐆(λ)$ is a Hecke algebra attached to the group $N_W(L)/L$, thus the dimension of the characters  of this group describe the multiplicities in the Harish-Chandra induced.

Similarly, when `𝐋` is a `ζ`-split Levi subgroup, and `λ` is a `d`-cuspidal unipotent  character of  `𝐋` then  (conjecturally) the $𝐆^F$-endomorphism algebra  of the Lusztig induced $R_𝐋^𝐆(λ)$  is a cyclotomic Hecke algebra for  to the  group $N_W(Lwϕ,λ)/L$.  The constituents  of $R_𝐋^𝐆(λ)$ are called  a  `ζ`-Harish-Chandra  series.  In  the  case of rational groups or cosets,  corresponding to finite  reductive groups, the  conjugacy class of `Lwϕ`  depends  only  on  the  order  `d`  of  `ζ`,  so  one  also talks of `d`-Harish-Chandra  series. These series correspond to `ℓ`-blocks where `l` is  a prime divisor of `Φ_d(q)` which  does not divide any other cyclotomic factor of the order of $𝐆^F$.

The functions  `relative_degrees, regular_eigenvalues, eigenspace_projector, position_regular_class, split_levis, cuspidal` in this module and the functions in the module `dSeries` allow to explore these situations.
