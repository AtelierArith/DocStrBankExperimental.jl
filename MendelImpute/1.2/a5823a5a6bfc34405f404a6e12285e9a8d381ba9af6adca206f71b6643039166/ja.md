```
phase(tgtfile::String, reffile::String, outfile::String; [impute::Bool],
    [phase::Bool], [dosage::Bool], [rescreen::Bool], [max_haplotypes::Int], 
    [stepwise::Int], [thinning_factor::Int], [scale_allelefreq::Bool], 
    [dynamic_programming::Bool])
```

MendelImputeプログラムのメイン関数。スライディングウィンドウを使用して、`reffile`のハプロタイププールから`tgtfile`のフェーズ（ハプロタイピング）を行い、結果を`outfile`に保存します。`tgtfile`内のすべてのSNPは`reffile`に存在する必要があります。各SNPの品質スコアは`outfile`に保存され、各サンプルのインピュテーションスコアは`sample.error`で終わるファイルに保存されます。

# 入力

  * `tgtfile`: VCF、PLINK、またはBGENファイル。VCFファイルは`.vcf`または`.vcf.gz`で終わる必要があります。PLINKファイルは`.bim/.bed/.fam`のトレーリングを除外する必要がありますが、トリオはすべて同じディレクトリに存在する必要があります。BGENファイルは`.bgen`で終わる必要があります。
  * `reffile`: `.jlso`で終わるリファレンスハプロタイプファイル（圧縮バイナリファイル）。[`compress_haplotypes`](@ref)を参照してください。
  * `outfile`: `.vcf.gz`、`.vcf`、または`.jlso`で終わる出力ファイル名。VCF出力の遺伝子型には欠損データがありません。`.jlso`で終わる場合、各サンプルの`HaplotypeMosaicPair`を記録する超圧縮データ構造が出力されます。

# オプション入力

  * `impute`: `true`の場合、`reffile`のすべてのSNPを`tgtfile`にインピュートします。そうでない場合、`tgtfile`の欠損SNPのみがインピュートされます。
  * `phase`: `true`の場合、すべての出力遺伝子型がフェーズされますが、観測データ（マイナーアレル数）が変更される可能性があります。`phase=false`の場合、すべての出力遺伝子型は非フェーズになりますが、観測されたマイナーアレル数は変更されません。
  * `dosage`: `true`の場合、ターゲット行列がインピュテーションのためのドージングであると仮定します。これは、遺伝子型行列が完全に単精度であることを意味します。
  * `rescreen`: このオプションは計算集約的ですが、より正確な結果を提供します。最小二乗目的を解く際に、いくつかのトップハプロタイプペアを保存し、観測データのみに対して最小二乗を再最小化します。
  * `max_haplotypes`: グローバル検索に使用するハプロタイプの最大数。このユニークなハプロタイプの数を超えるウィンドウは、ヒューリスティックを使用して検索されます。非ゼロの`stepscreen`または`thinning_factor`を指定する必要があります。
  * `stepwise`: 整数が指定されている場合、最初に`stepwise`のトップハプロタイプを見つけることによって最小二乗目的を解決し、その後、グローバル検索を使用して次のハプロタイプを見つけます。`max_haplotypes`を使用します。
  * `thinning_factor`: 整数が指定されている場合、`thining_factor`のユニークなハプロタイプのみに対して最小二乗目的を解決します。`max_haplotypes`を使用します。
  * `scale_allelefreq`: 希少SNPに対して`wᵢ = 1 / √2p(1-p)`でスケーリングされた重みを与えるかどうかを示すブール値。最大重みは2です。
  * `dynamic_programming`: すべてのウィンドウにわたって最長ハプロタイプストレッチを見つけるグローバル検索でフェーズを行うかどうかを示すブール値。（現在壊れています、申し訳ありません！）
