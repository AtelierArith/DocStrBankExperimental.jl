```
admixture_global(tgtfile::String, reffile::String, 
    refID_to_population::Dict{String, String}, populations::Vector{String})
```

`reffile`を使用して`tgtfile`内の各サンプルのグローバル祖先推定値を計算します。

# 入力

  * `tgtfile`: VCFまたはPLINKファイル。VCFファイルは`.vcf`または`.vcf.gz`で終わる必要があります。PLINKファイルは`.bim/.bed/.fam`のトレーリングを除外する必要がありますが、トリオはすべて同じディレクトリに存在する必要があります。
  * `reffile`: `.jlso`で終わる参照ハプロタイプファイル（圧縮バイナリファイル）。[`compress_haplotypes`](@ref)を参照してください。
  * `refID_to_population`: ハプロタイプ参照パネル内の各サンプルIDをその母集団の起源にマッピングする辞書。例については、[`thousand_genome_population_to_superpopulation`](@ref)および[`thousand_genome_samples_to_super_population`](@ref)の出力を参照してください。
  * `populations`: `values(refID_to_population)`に存在するユニークな母集団を含む`String`のベクター。

# オプション入力

  * `Q_outfile`: 推定された`Q`行列の出力ファイル名。デフォルトは`Q_outfile="mendelimpute.ancestry.Q"`。
  * `imputed_outfile`: `.jlso`で終わる補完された遺伝子型の出力ファイル名。デフォルトは`impute_outfile = "mendelimpute.ancestry.Q.jlso"`。

# 出力

  * `Q`: 推定された祖先の割合を含む`DataFrame`。各行はサンプルです。行列は`mendelimpute.ancestry.Q`に保存されます。
