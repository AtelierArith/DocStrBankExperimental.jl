```
struct EmbeddedDiscretization{Dc,T} <: AbstractEmbeddedDiscretization
```

この構造体は、カットモデルのための統合`Triangulation`を構築するために必要なすべての情報を含んでいます。

## コンストラクタ

```
cut(cutter::Cutter,background,geom)
```

## プロパティ

  * `bgmodel::DiscreteModel`: 背景メッシュ
  * `geo::CSG.Geometry`: 背景メッシュをカットするために使用されるジオメトリ
  * `subcells::SubCellData`: 背景メッシュに付随するカットされたサブセルのコレクション
  * `subfacets::SubFacetData`: 背景メッシュに付随するカットされたファセットのコレクション
  * `ls_to_bgcell_to_inoutcut::Vector{Vector{Int8}}`: ジオメトリツリーの各ノードに対して、背景メッシュ内の各セルのIN/OUT/CUT状態のリスト
  * `ls_to_subcell_to_inoutcut::Vector{Vector{Int8}}`: ジオメトリツリーの各ノードに対して、メッシュのカット部分内の各サブセルのIN/OUT/CUT状態のリスト
  * `ls_to_subfacet_to_inoutcut::Vector{Vector{Int8}}`: ジオメトリツリーの各ノードに対して、メッシュのカット部分内の各サブファセットのIN/OUT/CUT状態のリスト

## メソッド

  * [`Triangulation(cut::EmbeddedDiscretization,in_or_out)`](@ref)
  * [`EmbeddedBoundary(cut::EmbeddedDiscretization)`](@ref)
  * [`GhostSkeleton(cut::EmbeddedDiscretization)`](@ref)
