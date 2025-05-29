```
check_for_duplicates(log_volume_km3_vector::Union{Float64,Vector{Float64}}, InitialConc_H2O_vector::Union{Float64,Vector{Float64}}, InitialConc_CO2_vector::Union{Float64,Vector{Float64}}, log_vfr_vector::Union{Float64,Vector{Float64}}, depth_vector::Union{Float64,Vector{Float64}})::Nothing
```

この関数は、入力配列のいずれかに重複する要素が含まれているかどうかをチェックします。重複が見つかった場合、どの引数に重複があるかを示すエラーを発生させます。

  * この関数は `chamber` 関数内で使用されます。
