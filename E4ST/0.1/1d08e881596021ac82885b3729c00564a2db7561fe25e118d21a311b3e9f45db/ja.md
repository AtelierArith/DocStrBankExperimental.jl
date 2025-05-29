```
add_results_formula!(data, table_name::Symbol, result_name::Symbol, formula::String, unit::Type{<:Unit}, description::String)
```

結果を計算するために使用できる式を追加します。 [`compute_result`](@ref)を参照してください。これは[`AggregationTemplate`](@ref)および[`YearlyTable`](@ref)でも使用されます。

引数:

  * `data`
  * `table_name` - 結果が計算されるテーブルの名前。直接または他の結果の組み合わせとして。
  * `result_name` - 計算される結果の名前。テーブル内の列名であってはなりません。
  * `formula` - `formula`は2つの異なる形式を取ることができます。

      * `table_name`から直接集約される列の組み合わせであることができます。すなわち、`"SumHourly(vom, egen)"`。 [`Sum`](@ref)、[`SumHourly`](@ref)、[`SumYearly`](@ref)、[`AverageYearly`](@ref)、[`MinHourly`](@ref)を参照してください。ここでの列は、列名または`data`に保存された変数名（例: `dam_co2`）であることができます。
      * 他の結果の組み合わせでもあります。すなわち、`"(vom_cost + fuel_cost) / egen_total"`。
  * `unit` - 結果の数値の[`Unit`](@ref)
  * `description` - 計算の簡単な説明。
