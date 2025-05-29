これは、*有限生成群*の*表現*に関するGAP3/VkCurve機能のポートです。

有限生成群に対して、表現を有限生成群に変換できるように、十分な機能を定義しました。焦点は表現にあり、目的はそれらを簡素化することです。

有限生成群の要素は`AbsWord`または抽象語であり、自由群の要素を表します。

```julia-repl
julia> @AbsWord a,b,c,d,e,f # a=AbsWord(:a);b=AbsWord(:b)...

julia> F=FpGroup([a,b,c,d,e,f])
FreeGroup(a,b,c,d,e,f)

julia> G=F/[a^2,b^2,d*f^-1,e^2,f^2,a*b^-1*c,a*e*c^-1,b*d^-1*c,c*d*e^-1,a*f*c^-2,c^4]
FreeGroup(a,b,c,d,e,f)/[a²,b²,df⁻¹,e²,f²,ab⁻¹c,aec⁻¹,bd⁻¹c,cde⁻¹,afc⁻²,c⁴]

julia> simplify(F) # このパッケージの主な機能
Presentation: 2 generators, 4 relators, total length 16
Presentation: 2 generators, 3 relators, total length 10
FreeGroup(a,c)/[a²,ac⁻¹ac⁻¹,c⁴]
```

簡素化は以下のプロセスによって行われます：

```julia-rep1
julia> P=Presentation(G);simplify(P);G=FpGroup(P)
```

関数`Presentation`と`FpGroup`は、有限生成群から表現を作成し、その逆も行います。

アルゴリズムを高速化するために、表現の関係は内部的に`AbsWord`ではなく、*Tietze words*と呼ばれる正または負の生成子番号のリストで表されます。ここに、表現を探索するためのいくつかの関数を含む別の例があります。

```julia-repl
julia> @AbsWord a,b 

julia> F=FpGroup([a,b])
FreeGroup(a,b)

julia> G=F/[a^2,b^7,comm(a,a^b),comm(a,a^(b^2))*inv(b^a)]
FreeGroup(a,b)/[a²,b⁷,a⁻¹b⁻¹a⁻¹bab⁻¹ab,a⁻¹b⁻²a⁻¹b²ab⁻²ab²a⁻¹b⁻¹a]

julia> P=Presentation(G) # デフォルトで要約を表示
Presentation: 2 generators, 4 relators, total length 30

julia> relators(P)
4-element Vector{AbsWord}:
 a²
 b⁷
 ab⁻¹abab⁻¹ab
 b⁻²ab²ab⁻²ab²ab⁻¹
```

```julia-rep1
julia> showgens(P)
1. a 10 occurrences involution
2. b 20 occurrences

julia> dump(P) # ここでは関係の逆は大文字で表されます
# F 関係
1:3 aa
2:0 bbbbbbb
3:0 aBabaBab
4:0 abbaBBabbaBBB
gens=AbsWord[a, b] involutions:AbsWord[a] modified=false numredunds=0

julia> display_balanced(P)
1: a=A
2: bbbbbbb=1
3: aBab=BAbA
4: BBabbaBBabbaB=1

julia> P=tryconjugate(P) # 生成子を共役にしようとする
Presentation: 2 generators, 4 relators, total length 30
Bab=> Presentation: 2 generators, 3 relators, total length 28
# BabはPresentation: 2 generators, 3 relators, total length 28を与えます
Presentation: 2 generators, 3 relators, total length 28

julia> FpGroup(P) # やや簡素化された群
FreeGroup(a,b)/[b⁷,bab⁻¹abab⁻¹a,b⁻¹ab²ab⁻²ab²ab⁻²]
```

詳細については、`AbsWord, FpGroup, Presentation, relators, display_balanced, simplify, conjugate, tryconjugate`のヘルプ文字列を参照してください。

このパッケージに追加する最小限のものは、コクセター・トッドアルゴリズムです。
