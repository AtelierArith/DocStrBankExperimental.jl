`left_cells(W[,i])` は、1パラメータのヘッケ代数 `hecke(W,q)` の `i` 番目の両側セルにおける `W` の左セルを返します。

このプログラムは、例外的なタイプおよびタイプ `:A` に対して事前に計算されたデータ（[Geck-Halls 2014](biblio.htm#GH14)を参照）を使用しているため、これらのタイプに対しては非常に高速です（タイプ `E₈` の 101796 左セルを計算するのに 13 秒かかります）。他のタイプについては、左セルは基本原理から計算されるため、多くのカズダン-ルスティグ多項式を計算します。例えば、タイプ `D₆` の左セルを計算するのに 30 秒かかります。

```julia-repl
julia> W=coxgroup(:G,2)
G₂

julia> left_cells(W)
4-element Vector{LeftCell{FiniteCoxeterGroup{Perm{Int16},Int64}}}:
 LeftCell<G₂: duflo= character=φ₁‚₀>
 LeftCell<G₂: duflo=12 character=φ₁‚₆>
 LeftCell<G₂: duflo=2 character=φ₂‚₁+φ′₁‚₃+φ₂‚₂>
 LeftCell<G₂: duflo=1 character=φ₂‚₁+φ″₁‚₃+φ₂‚₂>
```

このようなレコードを印刷すると、左セルによって与えられるキャラクターとそのダフロ反転が表示されます。ダフロ反転 `r` は、`1:nref(W)` の部分集合 `I` として印刷され、`r=longest(reflection_subgroup(W,I))` となります。詳細は `describe_involution` を参照してください。

第二の引数 `i` が与えられた場合、プログラムは `i` 番目の両側セルにある左セルのみを返します。つまり、そのキャラクターが `W` の `i` 番目のファミリーに属する左セルです（[`Families`](@ref)を参照）。

```julia-repl
julia> W=coxgroup(:G,2);
julia> left_cells(W,1)
2-element Vector{LeftCell{FiniteCoxeterGroup{Perm{Int16},Int64}}}:
 LeftCell<G₂: duflo=2 character=φ₂‚₁+φ′₁‚₃+φ₂‚₂>
 LeftCell<G₂: duflo=1 character=φ₂‚₁+φ″₁‚₃+φ₂‚₂>
```
