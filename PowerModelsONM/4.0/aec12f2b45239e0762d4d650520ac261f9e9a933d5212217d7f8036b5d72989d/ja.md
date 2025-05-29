```
get_voltage_min_mean_max(
    solution::Dict{String,<:Any},
    data::Dict{String,<:Any};
    make_per_unit::Bool=true
)::Tuple{Real,Real,Real}
```

ネットワーク全体の電圧の最小値、平均値、最大値を計算します（マルチネットワークではありません）。

`data` は、`make*per*unit` が真であり、データがすでにパーユニットでない場合に、単位をパーユニットに変換するために使用されます。

`make_per_unit`（デフォルト: true）が真の場合、パーユニット表現で電圧統計を返します。`make_per_unit` が偽で、ネットワーク全体で異なる電圧ベースがある場合、統計は意味を成しません。
