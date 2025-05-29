```
mutable struct Node
    name::Symbol
    organisms::DataStructures.OrderedDict{Type{<:Species}, Organism}
    temperature::Temperature
    location::Tuple{Float64,Float64}
end
```

単一の空間ノードのデータ。

# 引数

  * `name::Symbol`: ノードの名前、通常は位置に関連する。
  * `organisms::DataStructures.OrderedDict{Type{<:Species}, Organism}`: ノードに生息するすべての種のデータを含む辞書。
  * `temperature::Temperature`: 温度に関する気候の仕様。
  * `location::Tuple{Float64,Float64}`: 座標によって示される地理的位置。
