```
struct GradedSpace{I<:Sector, D} <: ElementarySpace
    dims::D
    dual::Bool
end
```

ラベルの集合 `I` に対応する直和構造を持つ複素ユークリッド空間であり、そのオブジェクトはモニドの構造を持ち、モニダル積 `⊗` に関して定義されます。実際には、ラベル集合を `I<:Sector` 型のスーパーセレクションセクターの集合に制限します。例えば、有限またはコンパクト群の異なる不変表現の集合や、ユニタリーかつピボタルな（前）融合カテゴリの単純オブジェクトの同型類などです。

ここで `dims` は、各セクターの縮退または重複度を表します。

`dims` のデータ構造 `D` は、`Base.IteratorElsize(values(I))` の結果に依存します。結果が `HasLength` または `HasShape` 型である場合、`dims` は `NTuple{N,Int}` に格納され、`N = length(values(I))` となります。これは、セクター `s::I` が `s == getindex(values(I), i)` を通じてインデックスに変換でき、`i == findindex(values(I), s)` が成り立つことを要求します。もし `Base.IteratorElsize(values(I))` の結果が `IsInfinite()` または `SizeUnknown()` である場合、非ゼロの縮退次元を対応するセクターをキーとして格納するために `SectorDict{I,Int}` が使用されます。パラメータ `D` はユーザーから隠されており、通常は気にする必要はありません。

正しい `D` を持つ具体的な型 `GradedSpace{I,D}` は `Vect[I]` として得られるか、あるいは `I == Irrep[G]` の場合、`Rep[G]` として得られます。
