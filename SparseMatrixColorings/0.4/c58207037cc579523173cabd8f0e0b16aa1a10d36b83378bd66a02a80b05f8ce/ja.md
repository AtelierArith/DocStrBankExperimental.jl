```
GreedyColoringAlgorithm{decompression} <: ADTypes.AbstractColoringAlgorithm
```

疎行列のための貪欲彩色アルゴリズムで、列または行を順番に色付けし、設定可能な順序に従います。

これは、主関数[`coloring`](@ref)に引数として渡されます。

# コンストラクタ

```
GreedyColoringAlgorithm{decompression}(order=NaturalOrder(); postprocessing=false)
GreedyColoringAlgorithm(order=NaturalOrder(); postprocessing=false, decompression=:direct)
```

  * `order::AbstractOrder`: 列または行が色付けされる順序で、色の数に影響を与える可能性があります。
  * `postprocessing::Bool`: 中立色`0`をいくつかの頂点に割り当てることによって色付けが洗練されるかどうか。
  * `decompression::Symbol`: `:direct`または`:substitution`のいずれか。通常、`:substitution`は色の数を減らしますが、より高価な色付け（および復元）のコストがかかります。`:substitution`が適用できない場合は、`:direct`復元にフォールバックします。

!!! warning
    2番目のコンストラクタ（キーワード引数に基づく）は型不安定です。


# ADTypes 彩色インターフェース

`GreedyColoringAlgorithm`は[`ADTypes.AbstractColoringAlgorithm`](@extref ADTypes.AbstractColoringAlgorithm)のサブタイプであり、次のメソッドも適用可能です：

  * [`ADTypes.column_coloring`](@extref ADTypes.column_coloring)
  * [`ADTypes.row_coloring`](@extref ADTypes.row_coloring)
  * [`ADTypes.symmetric_coloring`](@extref ADTypes.symmetric_coloring)

詳細については、それぞれのドキュメント文字列を参照してください。

# 参照

  * [`AbstractOrder`](@ref)
  * [`decompress`](@ref)
