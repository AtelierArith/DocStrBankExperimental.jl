`HeckeCoset`s  are  `Hϕ`  where  `H`  is  an  Iwahori-Hecke algebra of some Coxeter  group `W` on which the automorphism `ϕ` of some Spets `Wϕ` acts by `ϕ(T_w)=T_{ϕ(w)}`.  For Weyl groups, this corresponds  to the action of the Frobenius  automorphism  on  the  commuting  algebra  of the induced of the trivial  representation from the  rational points of  some `F`-stable Borel subgroup to `𝐆 ^F`.

```julia-repl
julia> WF=rootdatum(:u,3)
u₃

julia> HF=hecke(WF,Pol(:v)^2;rootpara=Pol())
hecke(u₃,v²,rootpara=v)

julia> CharTable(HF)
CharTable(hecke(u₃,v²,rootpara=v))
┌───┬──────────┐
│   │ 111 21  3│
├───┼──────────┤
│111│  -1  1 -1│
│21 │-2v³  .  v│
│3  │  v⁶  1 v²│
└───┴──────────┘
```

Thanks  to the work of Xuhua He and Sian Nie, 'class_polynomials' also make sense for these cosets. This is used to compute such character tables.
