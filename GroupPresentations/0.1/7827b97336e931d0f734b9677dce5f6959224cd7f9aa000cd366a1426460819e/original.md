`tryconjugate(p[,goal[,printlevel]])`

This program tries to simplify group presentations by applying conjugations to  the  generators.  The  algorithm  depends  on  random  numbers,  and on tree-searching,  so is  not reproducible.  By default  the program stops as soon  as a shorter presentation is found.  Sometimes this does not give the desired  presentation.  One  can  give  a  second argument `goal`, then the program  will only stop when  a presentation of length  less than `goal` is found.  Finally, a third  argument can be  given and then all presentations the  programs runs  over which  are of  length less  than or  equal to this argument are displayed. Due to the non-deterministic nature of the program, it  may be useful to  run it several times  on the same input. Upon failure (to improve the presentation), the program returns `p`.

```julia-rep1
julia> display_balanced(p)
1: ba=ab
2: dbd=bdb
3: cac=aca
4: bcb=cbc
5: dAca=Acad
6: dcdc=cdcd
7: adad=dada
8: dcDbdc=bdcbdB
9: dcdadc=adcdad
10: adcDad=dcDadc
11: BcccbdcAb=dcbACdddc
julia> p=tryconjugate(p)
Presentation: 4 generators, 11 relators, total length 100
dcD=> Presentation: 4 generators, 10 relators, total length 90
# dcD gives Presentation: 4 generators, 10 relators, total length 90
Presentation: 4 generators, 10 relators, total length 90

julia> p=tryconjugate(p)
Dcd=> Presentation: 4 generators, 10 relators, total length 88
# Dcd gives Presentation: 4 generators, 10 relators, total length 88
Presentation: 4 generators, 10 relators, total length 88

julia> p=tryconjugate(p)
dcD=> Presentation: 4 generators, 10 relators, total length 90
Dbd=> Presentation: 4 generators, 10 relators, total length 96
Aca=> Presentation: 4 generators, 9 relators, total length 84
Presentation: 4 generators, 8 relators, total length 76
# Aca gives Presentation: 4 generators, 8 relators, total length 76
Presentation: 4 generators, 8 relators, total length 76

julia> p=tryconjugate(p)
Bcb=> Presentation: 4 generators, 8 relators, total length 70
# Bcb gives Presentation: 4 generators, 8 relators, total length 70
Presentation: 4 generators, 8 relators, total length 70

julia> p=tryconjugate(p)
Cac=> Presentation: 4 generators, 8 relators, total length 64
# Cac gives Presentation: 4 generators, 8 relators, total length 64
Presentation: 4 generators, 8 relators, total length 64

julia> p=tryconjugate(p)
caC=> Presentation: 4 generators, 8 relators, total length 58
# caC gives Presentation: 4 generators, 8 relators, total length 58
Presentation: 4 generators, 8 relators, total length 58

julia> p=tryconjugate(p)
Cac=> Presentation: 4 generators, 8 relators, total length 64
Cbc=> Presentation: 4 generators, 7 relators, total length 50
# Cbc gives Presentation: 4 generators, 7 relators, total length 50
Presentation: 4 generators, 7 relators, total length 50

julia> p=tryconjugate(p)
cdC=> Presentation: 4 generators, 7 relators, total length 56
Dcd=> Presentation: 4 generators, 7 relators, total length 54
Cac=> Presentation: 4 generators, 7 relators, total length 48
# Cac gives Presentation: 4 generators, 7 relators, total length 48
Presentation: 4 generators, 7 relators, total length 48

julia> p=tryconjugate(p)
caC=> Presentation: 4 generators, 7 relators, total length 50
Cdc=> Presentation: 4 generators, 7 relators, total length 50
Dbd=> Dcd=> Presentation: 4 generators, 7 relators, total length 60
Bab=> Aba=> Aca=> Presentation: 4 generators, 7 relators, total length 46
# Aca gives Presentation: 4 generators, 7 relators, total length 46
Presentation: 4 generators, 7 relators, total length 46

julia> display_balanced(p)
1: db=bd
2: ba=ab
3: cac=aca
4: ada=dad
5: bcb=cbc
6: cdcd=dcdc
7: AdCacd=cAdCac
```
