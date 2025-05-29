```
trajgwas(nullmeanformula, reformula, nullwsvarformula, idvar, covfile, geneticfile; kwargs...)
trajgwas(nullmeanformula, reformula, nullwsvarformula, idvar, df, geneticfile; kwargs...)
trajgwas(fittednullmodel, geneticfile; kwargs...)
trajgwas(fittednullmodel, bedfile, bimfile, bedn; kwargs...)
trajgwas(fittednullmodel, vcffile, nsamples, vcftype; kwargs...)
trajgwas(fittednullmodel, bgenfile, nsamples; kwargs...)
```

# 位置引数

  * `nullmeanformula::FormulaTerm`: nullモデルの平均式 (β)。
  * `reformula::FormulaTerm`: モデルのランダム効果式 (γ)。
  * `nullwsvarformula::FormulaTerm`: nullモデルの被験者内分散式 (τ)。
  * `idvar::Union{String, Symbol}`: グループ化のためのID変数。
  * `covfile::AbstractString`: ヘッダー行が1行ある共変量ファイル (csv)。1列は縦断的表現型である必要があります。
  * `df::DataFrame`: nullモデルの応答と回帰変数を含むDataFrame。
  * `geneticfile::Union{Nothing, AbstractString}`: GWASのための遺伝情報を含むファイル。このファイルには、.bed、.fam、または.bim拡張子なしのPLINKファイル名、または.vcf拡張子なしのVCFファイルが含まれます。`geneticfile==nothing`の場合、nullモデルのみが適合されます。`geneticfile`が提供されると、同じ`geneticfile`プレフィックスを持つbed、bim、famファイル（またはvcf）が存在する必要があります。gzやbz2などの圧縮ファイル形式が許可されています。すべての許可された形式は`SnpArrays.ALLOWED_FORMAT`で確認してください。VCFファイルを使用している場合は、`geneticformat = "VCF"`キーワードオプションを使用し、`vcftype`コマンドで用量(:DS)または遺伝子型(:GT)データを指定してください。
  * `fittednullmodel::StatsModels.TableRegressionModel`: `trajgwas(nullformula, covfile)`または`trajgwas(nullformula, df)`からの適合したnullモデルの出力。**注意** nullモデルが`bedfile, bimfile, bedn`または`vcffile, nsamples, vcftype`引数で渡される場合、nullモデルのID/データはPLINK/VCFファイルのIDの順序と一致する必要があります。
  * `bedfile::Union{AbstractString,IOStream}`: 完全なファイル名を持つPlink bedファイルへのパス。
  * `bimfile::Union{AbstractString,IOStream}`: 完全なファイル名を持つPlink bimファイルへのパス。
  * `bedn::Integer`: bed/vcfファイル内のサンプル数。

# キーワード引数

  * `analysistype`::AbstractString: 実施する分析のタイプ。デフォルトは`singlesnp`。他のオプションは`snpset`と`gxe`。
  * `geneticformat`::AbstractString: 遺伝分析に使用されるファイルのタイプ。現在サポートされているのは`"PLINK"`と`"VCF"`。デフォルトはPLINK。
  * `vcftype`::Union{Symbol, Nothing}: GWAS分析のためにVCFファイルから抽出するデータ。用量のための`:DS`または遺伝子型のための`:GT`。デフォルトはnothing。
  * `nullfile::Union{AbstractString, IOStream}`: 適合したnullモデルの出力ファイル; デフォルトは`trajgwas.null.txt`。
  * `pvalfile::Union{AbstractString, IOStream}`: gwas p値の出力ファイル; デフォルトは`trajgwas.pval.txt`。
  * `covtype::Vector{DataType}`: `covfile`の型情報。これは`CSV.read(covarfile)`にパースエラーがある場合に便利です。
  * `covrowinds::Union{Nothing,AbstractVector{<:Integer}}`: 共変量ファイルのサンプルインデックス。
  * `testformula::FormulaTerm`: テストユニットの式。デフォルトは`@formula(trait ~ 0 + snp)`。
  * `test::Symbol`: `:score`（デフォルト）または`:wald`。
  * `disable_wsvar::Bool`: Waldテストのための被験者内変動性のテストを無効にします。デフォルトはfalse。
  * `link::GLM.Link`: `LogitLink()`（デフォルト）、`ProbitLink()`、`CauchitLink()`、または`CloglogLink()`。
  * `snpmodel`: `ADDITIVE_MODEL`（デフォルト）、`DOMINANT_MODEL`、または`RECESSIVE_MODEL`。
  * `snpinds::Union{Nothing,AbstractVector{<:Integer}}`: bed/vcfファイルのSNPインデックス。
  * `geneticrowinds::Union{Nothing,AbstractVector{<:Integer}}`: bed/vcfファイルのサンプルインデックス。
  * `samplepath::Union{Nothing, AbstractString}`: BGENファイルにエンコードされていない場合のBGENサンプルファイルのパス。
  * `solver`: MathOptInterfaceによってサポートされている最適化ツール。デフォルトは`Ipopt.Optimizer()`。
  * `solver_config`: 最適化ツールのための設定キーと値の辞書。デフォルトは`Dict("print_level" => 0, "mehrotra_algorithm" => "yes", "warm_start_init_point" => "yes", "max_iter" => 100)`。
  * `runs::Integer`: nullモデルのための加重NLSの実行回数; デフォルトは2。各実行は最新の`m.τ`と`m.Lγ`を使用して重み行列`Vi`を更新し、新しい加重NLSを解決します。
  * `parallel::Bool`: nullモデルの適合のためのマルチスレッド。デフォルトは`false`。
  * `verbose::Bool`: デフォルトは`false`。
  * `snpset::Union{Nothing, Integer, AbstractString, AbstractVector{<:Integer}}`: snpset分析を実施する場合のみ含めます。整数はSNPのウィンドウを示します（すなわち、500 SNPごと）。抽象文字列を使用すると、ヘッダーがなく、スペースで区切られた2列の入力ファイルを指定できます。最初の列にはsnpset IDが含まれ、2番目の列にはbimfileと同一のsnpidが含まれている必要があります。AbstractVectorを使用すると、1つの共同snpsetテストを実施するためのSNPを指定できます。
  * `e::Union{AbstractString,Symbol}`: GxE分析を実施する場合のみ含めます。GxE相互作用をテストするために使用される環境変数。たとえば、`sex & snp`の相互作用をテストする場合は、`:sex`または`"sex"`を使用します。

# 例

以下は、PLINKファイルを使用した基本的なGWASの例です：

```julia
plinkfile = "plinkexample"
covfile = "covexample"
trajgwas(@formula(trait ~ sex), covfile, plkfile)
```

以下は、用量の後に遺伝子型を使用したVCFファイルを使用した基本的なGWASの例です：

```julia
vcffile = "vcfexample"
covfile = "covexample"
trajgwas(@formula(trait ~ sex), covfile, vcffile;
    geneticfile = "VCF", vcftype = :DS)

trajgwas(@formula(trait ~ sex), covfile, vcffile;
    geneticfile = "VCF", vcftype = :GT)
```

以下は、snpset GWAS（50 SNPごと）の例です。snpset分析の他のタイプについては、ドキュメントを参照してください：

```julia
trajgwas(@formula(trait ~ sex), covfile, plkfile;
    analysistype = "snpset", snpset = 50)
```

以下は、相互作用効果をテストするGxE GWASの例です：

```julia
trajgwas(@formula(trait ~ sex), covfile, plkfile;
    analysistype = "gxe", e = :sex)
```
