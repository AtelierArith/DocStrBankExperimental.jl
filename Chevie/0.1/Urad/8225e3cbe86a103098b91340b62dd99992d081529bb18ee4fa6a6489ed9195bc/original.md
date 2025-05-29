A  `struct UnipotentGroup` represents  the unipotent  radical `𝐔` of a Borel subgroup of a reductive group `G`.

See   [Carter1972,  section  4.2](biblio.htm#Car72b)  for  details  on  the following.  A Chevalley basis  of the Lie  algebra of `𝐔`  is a basis `eᵣ`, where   each  `eᵣ`  is  in  the  corresponding  root  subspace,  such  that `[eᵣ,eₛ]=Nᵣₛ e_{r+s}` for some integer constants `Nᵣₛ`. The constants `Nᵣₛ` for general roots are computed from the case where `r` and `s` are positive roots whose sum is a root; such a pair `(r,s)` is called *special*.

Constants  `Cᵣₛᵢⱼ` are defined, see [Carter1972, 5.2.3](biblio.htm#Car72b), by

$u_s(u)u_r(t)=u_r(t)u_s(u)\prod_{i,j>0}u_{ir+js}(C_{rsij}(-t)^iu^j)$

Where  `ir+js` runs over the positive  integral combinations of `r` and `s` which  are roots,  taken in  lexicographic order  on `(i,j)`. The constants `Cᵣₛᵢⱼ`  are computed from the constants  `Nᵣₛ`, see [Carter1972, bottom of page 61 and top of page 76](biblio.htm#Car72b).

The fields of `struct Unipotent Group` are:

  * `W`:         the Weyl group of `G`
  * `order`:     the total order on the roots used to normalize products of root subgroups (by default `1:nref(W)`)
  * `special:    a`NamedTuple`for each special pair of roots`(r,s)`
  * `r`  index of `r`
  * `s`  index of `s`
  * `rs` index of `r+s`
  * `N`: the constant `Nᵣₛ`
  * `comm`: stores the `Cᵣₛᵢⱼ` as the list of quadruples `(i,j,ir+js,Cᵣₛᵢⱼ)`.

```julia-repl
julia> U=UnipotentGroup(coxgroup(:G,2))
UnipotentGroup(G₂)

julia> U.special
10-element Vector{@NamedTuple{r::Int64, s::Int64, rs::Int64, N::Int64, comm::Vector{NTuple{4, Int64}}}}:
 (r = 1, s = 2, rs = 3, N = 1, comm = [(1, 1, 3, 1), (1, 2, 4, -1), (1, 3, 5, 1), (2, 3, 6, 2)])
 (r = 2, s = 3, rs = 4, N = 2, comm = [(1, 1, 4, 2), (2, 1, 5, 3), (1, 2, 6, -3)])
 (r = 2, s = 4, rs = 5, N = 3, comm = [(1, 1, 5, 3)])
 (r = 1, s = 5, rs = 6, N = 1, comm = [(1, 1, 6, 1)])
 (r = 3, s = 4, rs = 6, N = 3, comm = [(1, 1, 6, 3)])
 (r = 2, s = 1, rs = 3, N = -1, comm = [(1, 1, 3, -1), (2, 1, 4, -1), (3, 1, 5, -1), (3, 2, 6, -1)])
 (r = 3, s = 2, rs = 4, N = -2, comm = [(1, 1, 4, -2), (2, 1, 6, -3), (1, 2, 5, 3)])
 (r = 4, s = 2, rs = 5, N = -3, comm = [(1, 1, 5, -3)])
 (r = 5, s = 1, rs = 6, N = -1, comm = [(1, 1, 6, -1)])
 (r = 4, s = 3, rs = 6, N = -3, comm = [(1, 1, 6, -3)])
```
