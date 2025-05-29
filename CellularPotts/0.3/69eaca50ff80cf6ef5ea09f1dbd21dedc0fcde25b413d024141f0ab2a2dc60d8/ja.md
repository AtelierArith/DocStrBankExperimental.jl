```
CellState(
names::AbstractVector{S},
volumes::AbstractVector{T},
counts::AbstractVector{T};
options...) where {S<:Symbol, T<:Integer}


CellState(;names::AbstractVector{Symbol}, volumes::AbstractVector{T}, counts::AbstractVector{T}, options...) where T<:Integer
```

新しい `CellState` を作成します。各行は細胞に対応します。

デフォルトでは、この関数は以下の列を持つテーブルを生成します：

  * names`::Vector{Symbol}` – 細胞に与えられた名前のリスト（例： `:TCell`）
  * cellIDs`::Vector{<:Integer}` – 細胞に与えられた一意の番号
  * typeIDs`::Vector{<:Integer}` – 細胞の名前に対応する番号
  * volumes`::Vector{<:Integer}` – 占有されているグリッドの平方数
  * desiredVolumes`::Vector{<:Integer}`– 希望するグリッドの平方数
  * perimeters`::Vector{<:Integer}`– 細胞の境界ペナルティ
  * desiredPerimeters`::Vector{<:Integer}`– 希望する細胞の境界ペナルティ

テーブルの最初の行は `:Medium` に予約されており、これはどの細胞にも属さないグリッドの位置に与えられた名前で、インデックスは0です（最初の細胞にはインデックス1が与えられます）。

追加の細胞プロパティはキーワード引数として提供できます。キーワード引数の長さは細胞の種類の数または総細胞数と一致する必要があります。      
