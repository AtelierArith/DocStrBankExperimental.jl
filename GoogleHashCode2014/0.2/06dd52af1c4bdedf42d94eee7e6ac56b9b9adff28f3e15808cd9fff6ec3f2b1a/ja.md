```
都市
```

[`Junction`](@ref)と[`Street`](@ref)で構成された都市を、追加のインスタンスパラメータと共に保存します。

`City`オブジェクトは、関数[`read_city`](@ref)を使用して構築できます。

# フィールド

  * `total_duration::Int`: 車の旅程に割り当てられた総時間（秒単位）
  * `nb_cars::Int`: フリート内の車の数
  * `starting_junction::Int`: すべての車が最初に位置するジャンクションのインデックス（インデックスはジャンクションのリスト内の位置を指します）
  * `junctions::Vector{Junction}`: ジャンクションのリスト
  * `streets::Vector{Street}`: ストリートのリスト

# 例

```jldoctest
julia> using GoogleHashCode2014

julia> city = read_city()
City with 11348 junctions and 17958 streets.
8 cars all start from junction 4517 and travel for at most 54000s.
    
julia> length(city.junctions)
11348
    
julia> length(city.streets)
17958

julia> city.starting_junction
4517

julia> city.junctions[10]  # get the junction object at junction index 10
Junction at coordinates (48.872250900000004, 2.3124588)

julia> city.streets[10]  # get the street object at street index 10
Bidirectional street between junction indices 6814 and 2728 - duration 13s, distance 187m
```
