```
ordinalgwas(nullformula, covfile, geneticfile; kwargs...)
ordinalgwas(nullformula, df, geneticfile; kwargs...)
ordinalgwas(fittednullmodel, geneticfile; kwargs...)
ordinalgwas(fittednullmodel, bedfile, bimfile, bedn; kwargs...)
```

# 位置引数

  * `nullformula::FormulaTerm`: 帰無モデルのための式。
  * `covfile::AbstractString`: ヘッダー行が1行ある共変量ファイル（csv）。1つの列は、1から始まる整数として符号化された順序表現型である必要があります。例えば、順序表現型は1、2、3、4として符号化できますが、0、1、2、3としては符号化できません。
  * `df::DataFrame`: 帰無モデルのための応答と回帰変数を含むDataFrame。
  * `geneticfile::Union{Nothing, AbstractString}`: GWASのための遺伝情報を含むファイル。このファイルには、.bed、.fam、または.bim拡張子のないPLINKファイル名または.vcf拡張子のないVCFファイルが含まれます。`geneticfile==nothing`の場合、帰無モデルのみが適合されます。`geneticfile`が提供される場合、同じ`geneticfile`プレフィックスを持つbed、bim、およびfamファイル（またはvcf）が存在する必要があります。gzやbz2などの圧縮ファイル形式が許可されています。すべての許可された形式は`SnpArrays.ALLOWED_FORMAT`で確認できます。VCFファイルを使用している場合は、`geneticformat = "VCF"`キーワードオプションを使用し、`vcftype`コマンドで用量(:DS)または遺伝子型(:GT)データを指定してください。
  * `fittednullmodel::StatsModels.TableRegressionModel`: `ordinalgwas(nullformula, covfile)`または`ordinalgwas(nullformula, df)`からの適合された帰無モデルの出力。
  * `bedfile::Union{AbstractString,IOStream}`: 完全なファイル名を持つPlink bedファイルへのパス。
  * `bimfile::Union{AbstractString,IOStream}`: 完全なファイル名を持つPlink bimファイルへのパス。
  * `bedn::Integer`: bed/vcfファイル内のサンプル数。

# キーワード引数

  * `analysistype`::AbstractString: 実施する分析のタイプ。デフォルトは`singlesnp`。他のオプションは`snpset`と`gxe`です。
  * `geneticformat`::AbstractString: 遺伝分析に使用されるファイルのタイプ。現在サポートされているのは`"PLINK"`、`"VCF"`、および`"BGEN"`です。デフォルトはPLINKです。
  * `vcftype`::Union{Symbol, Nothing}: GWAS分析のためにVCFファイルから抽出するデータ。用量のための`:DS`または遺伝子型のための`:GT`。デフォルトはnothingです。
  * `nullfile::Union{AbstractString, IOStream}`: 適合された帰無モデルの出力ファイル；デフォルトは`ordinalgwas.null.txt`です。
  * `pvalfile::Union{AbstractString, IOStream}`: gwas p値の出力ファイル；デフォルトは`ordinalgwas.pval.txt`です。
  * `covtype::Vector{DataType}`: `covfile`の型情報。これは、`CSV.read(covarfile)`にパースエラーがある場合に便利です。
  * `covrowinds::Union{Nothing,AbstractVector{<:Integer}}`: 共変量ファイルのサンプルインデックス。
  * `testformula::FormulaTerm`: テストユニットのための式。デフォルトは`@formula(trait ~ 0 + snp)`です。
  * `test::Symbol`: `:score`（デフォルト）または`:lrt`。
  * `link::GLM.Link`: `LogitLink()`（デフォルト）、`ProbitLink()`、`CauchitLink()`、または`CloglogLink()`。
  * `snpmodel`: `ADDITIVE_MODEL`（デフォルト）、`DOMINANT_MODEL`、または`RECESSIVE_MODEL`。
  * `snpinds::Union{Nothing,AbstractVector{<:Integer}}`: bed/vcfファイルのSNPインデックス。
  * `geneticrowinds::Union{Nothing,AbstractVector{<:Integer}}`: bed/vcfファイルのサンプルインデックス。
  * `samplepath::Union{Nothing, AbstractString}`: BGENファイルにエンコードされていない場合のBGENサンプルファイルのパス。
  * `solver`: MathOptInterfaceによってサポートされている最適化手法。デフォルトは`NLopt.Optimizer()`で、`algorithm=:LD_SLSQP`および`maxeval=4000`です。もう1つの一般的な選択肢は`Ipopt.Optimizer()`です。
  * `verbose::Bool`: デフォルトは`false`です。
  * `snpset::Union{Nothing, Integer, AbstractString, AbstractVector{<:Integer}}`: snpset分析を実施する場合のみ含めます。整数はSNPのウィンドウを示します（すなわち、500 SNPごと）。抽象文字列は、ヘッダーがなく、スペースで区切られた2列を持つ入力ファイルを指定することを可能にします。最初の列にはsnpset IDが含まれ、2番目の列にはbimfileと同一のsnpidが含まれている必要があります。AbstractVectorを使用すると、1つの共同snpsetテストを実行するためのSNPを指定できます。
  * `e::Union{AbstractString,Symbol}`: GxE分析を実施する場合のみ含めます。GxE相互作用をテストするために使用される環境変数。例えば、`sex & snp`の相互作用をテストする場合は、`:sex`または`"sex"`を使用します。

# 例

以下は、PLINKファイルを使用した基本的なGWASの例です：

```julia
plinkfile = "plinkexample"
covfile = "covexample"
ordinalgwas(@formula(trait ~ sex), covfile, plkfile)
```

以下は、用量の後に遺伝子型を使用したVCFファイルを使用した基本的なGWASの例です：

```julia
vcffile = "vcfexample"
covfile = "covexample"
ordinalgwas(@formula(trait ~ sex), covfile, vcffile; 
    geneticfile = "VCF", vcftype = :DS)

ordinalgwas(@formula(trait ~ sex), covfile, vcffile; 
    geneticfile = "VCF", vcftype = :GT)
```

以下は、snpset GWAS（50 SNPごと）の例です。snpset分析の他のタイプについては、ドキュメントを参照してください：

```julia
ordinalgwas(@formula(trait ~ sex), covfile, plkfile; 
    analysistype = "snpset", snpset = 50)
```

以下は、相互作用効果をテストするGxE GWASの例です：

```julia
ordinalgwas(@formula(trait ~ sex), covfile, plkfile;
    analysistype = "gxe", e = :sex)
```
