```
votemap(DataSets::Vector{GeoData}, criteria::Vector{String}, dims=(50,50,50))
```

異なる2D/3Dトモグラフィーデータセットにおける一貫した特徴を示す投票マップを作成します。

動作の仕組みは次のとおりです：

  * 異なるGeoDataセット間の共通領域を見つける（重複する経度/緯度/深度の領域）
  * すべてのDataSetsのフィールドを共通の座標に補間する
  * 1つのモデル内のデータポイントをフィルタリングする（例：速度異常が2パーセントを超える領域）。この基準を満たすものはすべて1に、その他は0に設定します。
  * 異なるデータセットの結果を合計する

異なるデータセット間で特徴が一貫している場合、それはより大きな値を持ちます。

# 例

2つの地震速度データセット `Data_Zhao_Pwave` と `DataKoulakov_Alps` があると仮定します：

```julia
julia> Data_Zhao_Pwave
GeoData
  size  : (121, 94, 101)
  lon   ϵ [ 0.0 : 18.0]
  lat   ϵ [ 38.0 : 51.95]
  depth ϵ [ -1001.0 km : -1.0 km]
  fields: (:dVp_Percentage,)
julia> DataKoulakov_Alps
  GeoData
    size  : (108, 81, 35)
    lon   ϵ [ 4.0 : 20.049999999999997]
    lat   ϵ [ 37.035928143712574 : 49.01197604790419]
    depth ϵ [ -700.0 km : -10.0 km]
    fields: (:dVp_percentage, :dVs_percentage)
```

次のようにして、2つのデータセットを組み合わせた投票マップを作成できます：

```julia
julia> Data_VoteMap = votemap([Data_Zhao_Pwave,DataKoulakov_Alps],["dVp_Percentage>2.5","dVp_percentage>3.0"])
GeoData
  size  : (50, 50, 50)
  lon   ϵ [ 4.0 : 18.0]
  lat   ϵ [ 38.0 : 49.01197604790419]
  depth ϵ [ -700.0 km : -10.0 km]
  fields: (:votemap,)
```

単一のデータセットの投票マップを作成することもできます：

```julia
julia> Data_VoteMap = votemap(Data_Zhao_Pwave,"dVp_Percentage>2.5", dims=(50,51,52))
GeoData
  size  : (50, 51, 52)
  lon   ϵ [ 0.0 : 18.0]
  lat   ϵ [ 38.0 : 51.95]
  depth ϵ [ -1001.0 km : -1.0 km]
  fields: (:votemap,)
```
