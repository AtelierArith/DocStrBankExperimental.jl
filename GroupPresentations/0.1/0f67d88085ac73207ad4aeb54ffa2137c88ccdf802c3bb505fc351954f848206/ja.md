`images(P::Presentation)`

もし `P` が生成子の画像と逆画像がすべてのティエッツ変換を通じて追跡されているプレゼンテーションである場合、`images` は現在の生成子の逆画像を古い生成子の単語として、古い生成子の画像を現在の生成子の単語として印刷します。

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
