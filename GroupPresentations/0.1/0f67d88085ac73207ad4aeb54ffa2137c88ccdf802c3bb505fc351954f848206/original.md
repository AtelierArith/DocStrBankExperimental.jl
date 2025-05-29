`images(P::Presentation)`

If  `P` is a presentation in which generator images and preimages are being traced  through all Tietze transformations  applied to `P`, `images` prints the  preimages of the current generators as words in the old generators and the images of the old generators as words in the current generators.

```julia-repl
julia> P=Presentation("
1: a=A
2: e=E
3: f=F
4: c=C
5: d=D
6: bbb=1
7: fc=CF
8: dc=CD
9: fe=EF
10: ec=CE
11: da=AF
12: ed=DE
13: fd=DF
14: ca=AE
15: ea=AC
16: fa=AD
17: fb=bE
18: Bcbfd=1
19: Bebfe=1
20: Bdbfedc=1
21: babab=ABABA
") 
Presentation: 6 generators, 21 relators, total length 84
julia> tracing(P)
julia> GroupPresentations.Go(P)
Presentation: 3 generators, 10 relators, total length 81

julia> P.imagesOldGens
6-element Vector{Vector{Int64}}:
 [1]
 [2]
 [1, -2, 1, 3, 1, 2, 1]
 [3]
 [-2, 1, 3, 1, 2]
 [1, 3, 1]

julia> P.preImagesNewGens
3-element Vector{Vector{Int64}}:
 [1]
 [2]
 [4]
```

```julia-rep1
julia> GroupPresentations.images(P)
current generators in terms of the old ones:
  a=a
  b=b
  d=d
old generators in terms of the current ones:
  a=a
  b=b
  c=ab⁻¹adaba
  d=d
  e=b⁻¹adab
  f=ada
```
