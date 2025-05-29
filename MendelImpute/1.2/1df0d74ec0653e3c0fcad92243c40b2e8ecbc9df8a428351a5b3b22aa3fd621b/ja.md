```
admixture_local(tgtfile::String, reffile::String, 
    refID_to_population::Dict{String, String}, populations::Vector{String},
    population_colors::Vector{RGB{FixedPointNumbers.N0f8}})
```

`tgtfile`内の各サンプルに対するグローバル祖先推定を、ラベル付きリファレンスパネル`reffile`を使用して計算します。

# 入力

  * `tgtfile`: VCFまたはPLINKファイル。VCFファイルは`.vcf`または`.vcf.gz`で終わる必要があります。PLINKファイルは`.bim/.bed/.fam`のトレーリングを除外する必要がありますが、トリオはすべて同じディレクトリに存在する必要があります。
  * `reffile`: `.jlso`で終わるリファレンスハプロタイプファイル（圧縮バイナリファイル）。[`compress_haplotypes`](@ref)を参照してください。
  * `refID_to_population`: ハプロタイプリファレンスパネル内の各サンプルIDをその母集団の起源にマッピングする辞書。例については、[`thousand_genome_population_to_superpopulation`](@ref)および[`thousand_genome_samples_to_super_population`](@ref)の出力を参照してください。
  * `population`: `values(refID_to_population)`に存在するユニークな母集団を含む`String`のリスト。
  * `population_colors`: 各母集団の色のベクトル。`typeof(population_colors}`は`Vector{RGB{FixedPointNumbers.N0f8}}`である必要があります。

# 出力

  * `Q`: 推定された祖先の割合を含む行列。各行はハプロタイプです。サンプル1のハプロタイプは行1と2にあり、サンプル2のものは行3、4...などにあります。
  * `pop_colors`: 色を格納する`Q`のサンプル次元を持つ行列。
