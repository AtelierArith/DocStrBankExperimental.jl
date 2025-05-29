```
composition(sample_phase::HaplotypeMosaicPair, panelID::Vector{String}, 
    refID_to_population::Dict{String, String}, [populations::Vector{String}])
```

サンプルの染色体構成をフェーズ情報に基づいて計算します。この関数は、個人の混合比率をより簡単にプロットするために使用されます。

# 入力

  * `sample_phase`: サンプルのフェーズ情報を格納する `HaplotypeMosaicPair`、ハプロタイプの開始位置とハプロタイプラベルを含みます。
  * `panelID`: 参照ハプロタイプパネル内のサンプルID
  * `refID_to_population`: ハプロタイプ参照パネル内の各サンプルIDをその人口起源にマッピングする辞書。例については、[`thousand_genome_population_to_superpopulation`](@ref) および [`thousand_genome_samples_to_super_population`](@ref) の出力を参照してください。

# オプションの入力

  * `populations`: `refID_to_population` に存在する人口のユニークなリスト

# 出力

  * `composition`: `composition[i]` が `populations[i]` からのサンプルの祖先（%）に等しいパーセンテージのリスト
