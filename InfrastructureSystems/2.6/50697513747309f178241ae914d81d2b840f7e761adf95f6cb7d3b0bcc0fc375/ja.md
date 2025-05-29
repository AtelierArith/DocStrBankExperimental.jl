```julia
copy_time_series!(
    dst::Union{InfrastructureSystems.InfrastructureSystemsComponent, InfrastructureSystems.SupplementalAttribute},
    src::Union{InfrastructureSystems.InfrastructureSystemsComponent, InfrastructureSystems.SupplementalAttribute};
    name_mapping,
    scaling_factor_multiplier_mapping
)

```

効率的に1つのコンポーネントのすべてのtime_seriesを別のコンポーネントにコピーして、基礎となる参照を追加します。

# 引数

  * `dst::TimeSeriesOwners`: 目的地のオーナー
  * `src::TimeSeriesOwners`: ソースのオーナー
  * `name_mapping::Dict = nothing`: オプションでsrcの名前を異なるdstの名前にマッピングします。提供され、srcに`time_series`があり、その名前が`name_mapping`に存在しない場合、その`time_series`はコピーされません。`name_mapping`がnothingの場合、すべての`time_series`はsrcの名前でコピーされます。
  * `scaling_factor_multiplier_mapping::Dict = nothing`: オプションでsrcの乗数を異なるdstの乗数にマッピングします。提供され、srcに`time_series`があり、その乗数が`scaling_factor_multiplier_mapping`に存在しない場合、その`time_series`はコピーされません。`scaling_factor_multiplier_mapping`がnothingの場合、すべての`time_series`はsrcの乗数でコピーされます。
