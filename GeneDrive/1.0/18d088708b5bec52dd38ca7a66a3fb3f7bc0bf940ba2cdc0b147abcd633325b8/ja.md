```
mutable struct Organism{S <: Species}
    gene_data::Genetics
    all_stages::DataStructures.OrderedDict{Type{<:LifeStage}, Stage}
end
```

種特有の遺伝子およびライフステージ情報のための汎用データコンテナ。

# 引数

  * `gene_data::Genetics`: 種および修飾特有の遺伝データ。
  * `all_stages::DataStructures.OrderedDict{Type{<:LifeStage}, Stage}`: 野生型種特有のライフステージデータの辞書。
