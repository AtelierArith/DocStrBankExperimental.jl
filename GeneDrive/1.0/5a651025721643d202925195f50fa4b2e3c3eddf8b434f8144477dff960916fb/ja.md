```
struct Network
    name::Symbol
    nodes::DataStructures.OrderedDict{Symbol,Node}
    migration::DataStructures.OrderedDict{DataType},Array{Matrix{Float64},2}}
    locations_key_map
end
```

複数の相互接続された空間ノードのデータ。

# 引数

  * `name::Symbol`: ネットワークの名前、通常は場所に関連する。
  * `nodes::DataStructures.OrderedDict{Symbol,Node}`: ネットワークに含まれるノードのデータの辞書（メタポピュレーション）。
  * `migration::DataStructures.OrderedDict{DataType}, Array{Matrix{Float64},2}}`: 種、遺伝子型、および段階特有の遷移率を定義するデータ。エントリはデフォルトでゼロ。
  * `locations_key_map`: ノードの位置情報のマッピング。遷移率を割り当てるために使用される。
