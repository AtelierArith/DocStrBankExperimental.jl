`simplify(G)`

`simplify` は、与えられた有限生成群 `G` の表現のコピーに対して Tietze 変換を適用し、生成子の数、関係の数、および関係の長さに関してそれを縮小します。

`simplify` は、結果として得られる有限生成群を返します（これは `G` と同型です）。

```julia-repl
julia> @AbsWord a,b,c,d,e,f

julia> F=FpGroup([a,b,c,d,e,f])
FreeGroup(a,b,c,d,e,f)

julia> G=F/[a^2,b^2,d*f^-1,e^2,f^2,a*b^-1*c,a*e*c^-1,b*d^-1*c,c*d*e^-1,a*f*c^-2,c^4]
FreeGroup(a,b,c,d,e,f)/[a²,b²,df⁻¹,e²,f²,ab⁻¹c,aec⁻¹,bd⁻¹c,cde⁻¹,afc⁻²,c⁴]

julia> simplify(G)
FreeGroup(a,c)/[a²,ac⁻¹ac⁻¹,c⁴]
```

実際、呼び出し

```julia-rep1
julia> simplify(G)
```

は、呼び出しシーケンスの省略形です。

```julia-rep1
julia> P=Presentation(G,0);simplify(P);FpGroup(P)
```

これは、中間表現 `P` に対してかなり単純な戦略の Tietze 変換を適用します。具体的な群に対して結果の表現が満足できない場合は、利用可能な Tietze 変換関数のより洗練されたインタラクティブな使用を試みるべきです（「Tietze 変換」を参照）。
