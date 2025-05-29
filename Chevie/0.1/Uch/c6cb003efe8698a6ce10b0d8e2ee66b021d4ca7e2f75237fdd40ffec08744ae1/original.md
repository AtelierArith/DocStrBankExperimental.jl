`deligne_lusztig_lefschetz(h,m=0)` or `dllefschetz(h,m=0)`

Here `h` is an element of a Hecke algebra associated to a Coxeter group `W` or  Coxeter coset `Wϕ` which itself is  associated to an algebraic group `𝐆`.  By [DigneMichel1985](biblio.htm#DM85),  for $g∈  𝐆^F$, the  number of fixed  points  of  `Fᵐ`  on  the  Deligne-Lusztig variety associated to the element `wϕ∈Wϕ`, have for `m` divisible by a sufficently large integer `d`, the  form $∑_φ φ_{(qᵐ)}(T_wϕ)R_φ(g)$ where  `φ` runs over the irreducible characters  of $Wϕ$, where $R_φ$ is the corresponding almost character, and   where  $φ_{(qᵐ)}$  is  a  character  value  of  the  Hecke  algebra $H(Wϕ,qᵐ)$  of $Wϕ$ with parameter `qᵐ`.  This expression is called the *Lefschetz  character* of the Deligne-Lusztig  variety. If we consider `qᵐ` as  an indeterminate `x`, it  can be seen as  a sum of unipotent characters with   coefficients  character   values  of   the  generic   Hecke  algebra $H(Wϕ,x)$.  A  more  complicated  formula  involving  the  eigenvalues of Frobenius  attached to  unipotent characters  applies for  `m` not prime to `d`.  The function  returns this  formula when  a second parameter `m≠0` is given.

The  function 'dllefschetz' takes  as argument a  Hecke element and returns the  corresponding Lefschetz character. This is defined on the whole of the Hecke  algebra by linearity.  The Lefschetz character  of various varieties related   to   Deligne-Lusztig   varieties,   like   their  completions  or desingularisation,  can be  obtained by  taking the  Lefschetz character at various elements of the Hecke algebra.

```julia-repl
julia> W=coxgroup(:A,2)
A₂

julia> H=hecke(W,Pol(:q))
hecke(A₂,q)

julia> T=Tbasis(H);

julia> dllefschetz(T(1,2))
[A₂]:<111>-q<21>+q²<3>

julia> dllefschetz((T(1)+T())*(T(2)+T()))
[A₂]:q<21>+(q²+2q+1)<3>
```

The   last  line  shows  the   Lefschetz  character  of  the  Samelson-Bott desingularisation of the Coxeter element Deligne-Lusztig variety.

We now show an example with a coset (corresponding to the unitary group).

```julia-repl
julia> H=hecke(spets(W,Perm(1,2)),Pol(:q)^2)
hecke(²A₂,q²)

julia> T=Tbasis(H);dllefschetz(T(1))
[²A₂]:-<11>-q<²A₂>+q²<2>
```

Finally,  there is a second form `dllefschetz(H::HeckeAlgebra,w,i=0)` where the  arguments are a Hecke algebra and an  element of `w`. This may be used for  Spetses where we know the column of the `CharTable` of `H` for `w` but not other columns of the spetsial Hecke algebra charcater table.
