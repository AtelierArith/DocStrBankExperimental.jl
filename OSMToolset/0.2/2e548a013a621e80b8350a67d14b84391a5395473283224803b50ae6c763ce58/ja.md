```
AttractivenessSpatIndex{T <: AbstractMetaPOI}(filename::AbstractString, get_range::Function=get_attractiveness_range, get_group::Function=get_attractiveness_group)
AttractivenessSpatIndex{T <: AbstractMetaPOI}(df::AbstractDataFrame, get_range::Function=get_attractiveness_range, get_group::Function=get_attractiveness_group)
```

CSVファイルまたはDataFrame内のデータに基づいて魅力的な空間インデックスを構築します。

`T`が`AttractivenessMetaPOI`型であると仮定すると、CSVファイルまたはDataFrameには以下の列が必要です：     - group - 魅力インデックス内のデータグループ、各グループ名が魅力の次元を作成します     - key - XMLファイル内のキー<tag>     - values - <tag>内の値（アスタリスク`"*"`はすべての値をキャッチします）     - influence - 影響の強さ     - range - メートル単位の最大影響範囲

`DataFrame`が提供されると、空間インデックス内の参照`LLA`座標のために追加のパラメータ`refLLA`を提供できます。空間インデックスはENU座標系で機能します。

`T`が提供されない場合、`AttractivenessMetaPOI`がデフォルトのメタデータ型として使用されます。

型`F`は、`get_group = (a::T) -> :somegroup`として提供される魅力グループ関数を表します。
