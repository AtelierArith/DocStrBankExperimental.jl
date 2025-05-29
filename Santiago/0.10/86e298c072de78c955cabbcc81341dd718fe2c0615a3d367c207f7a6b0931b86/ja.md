```julia
properties_dataframe(
    systems::Array{Santiago.System};
    massflow_selection
) -> Any

```

システムのプロパティを `DataFrame` に抽出します。

引数 `massflow_selection` を使用すると、質量流量計算からどの情報を抽出するかを選択できます。

注意: 技術ごとの質量流量（'tech_flows'）は DataFrame にエクスポートできません！JSON エクスポートを試してください。

### 例:

`massflow_selection = ["recovered | water | mean", "lost | water| air loss | q_0.5"]` これは、回収された水の平均値と空気に失われた水の50%分位点を抽出します。注意: 値の順序は、システムプロパティに保存されている `NamedArray` の次元と一致する必要があります！

`massflow_selection` を `"all"` に設定すると、すべての質量流量量（非常に多くあります！）を抽出できます。
