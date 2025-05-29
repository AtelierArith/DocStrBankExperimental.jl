```
plan_edf_to_onda_samples_groups(plan_rows; extra_onda_signal_groupby=())
```

`plan_rows`を`:sensor_type`、`:sample_unit`、`:sample_rate`、および`extra_onda_signal_groupby`列の値に基づいてグループ化し、各グループごとにユニークな`:sensor_label`を作成し、[`OndaEDF.promote_encodings`](@ref)を使用して各グループのOndaエンコーディングを昇格させます。同じ`:sensor_label`を持つすべての行は、[`edf_to_onda_samples`](@ref)によって単一のOnda Samplesに結合されます。

`:edf_signal_index`列が存在しない場合、または欠落している場合は、入力行の順序に基づいて埋められます。

更新された行は、最初にグループ化列で、次に入力行内の発生順でソートされて返されます。
