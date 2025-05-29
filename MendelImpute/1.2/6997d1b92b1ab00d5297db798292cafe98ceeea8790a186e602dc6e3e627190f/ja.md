```
paint(sample_phase::HaplotypeMosaicPair, panelID::Vector{String},
    refID_to_population::Dict{String, String}, populations::Vector{String})
```

個人のフェーズされたハプロタイプの長さをパーセンテージのセグメントに変換します。この関数は「ペイントされた染色体」をより簡単にプロットするために使用されます。

# 入力

  * `sample_phase`: サンプルのフェーズ情報を格納する `HaplotypeMosaicPair`、ハプロタイプの開始位置とハプロタイプラベルを含みます。
  * `panelID`: 参照ハプロタイプパネルのサンプルID
  * `refID_to_population`: ハプロタイプ参照パネルの各サンプルIDをその母集団の起源にマッピングする辞書。例については、[`thousand_genome_population_to_superpopulation`](@ref) および [`thousand_genome_samples_to_super_population`](@ref) の出力を参照してください。

# オプションの入力

  * `populations`: `refID_to_population` に存在する母集団のユニークなリスト

# 出力

  * `s1_composition`: ハプロタイプ1の構成は `s1_composition[1]` に格納されており、`sum(s1_composition[1]) == 1` となるパーセンテージのリストです。各セグメント `s1_composition[1][i]` の祖先は `s1_composition[2][i]` に格納されています。
  * `s2_composition`: ハプロタイプ2の構成は `s2_composition[1]` に格納されており、`sum(s2_composition[1]) == 1` となるパーセンテージのリストです。各セグメント `s2_composition[1][i]` の祖先は `s2_composition[2][i]` に格納されています。
