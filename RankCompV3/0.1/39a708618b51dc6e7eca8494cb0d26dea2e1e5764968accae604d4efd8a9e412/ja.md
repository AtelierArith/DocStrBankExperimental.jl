```
reoa(fn_expr::AbstractString = "fn_expr.txt",
       fn_meta::AbstractString = "fn_meta.txt")
```

RankCompV3は、遺伝子ペアの相対発現順序（REO）に基づく差次的発現解析アルゴリズムです。これは、バルクまたは単一細胞RNAシーケンシング（scRNA-seq）データ、マイクロアレイ遺伝子発現プロファイル、プロテオミクスプロファイルなどに適用できます。scRNA-seqデータに適用する場合、単一細胞モードまたは擬似バルクモードで実行できます。擬似バルクモードは、実行時間とメモリコストを削減しながら精度を向上させることが期待されています。

# 例

## クイックスタート

パッケージに付属の入力ファイルを使用してテストジョブを実行します。

```jldoctest
julia> using RankCompV3
# 以下の他のパラメータのデフォルト値を使用します。パラメータを変更する必要がある場合は、直接追加してください。
julia> result = reoa(use_testdata="yes")
```

分析結果といくつかのプロットが生成され、現在の作業ディレクトリに保存されます。また、`reoa`関数によって返され、返された値を変数に割り当てることでキャプチャできます。上記の例では`result`です。

最初の返り値はDataFrameで、行は遺伝子、列は各遺伝子の統計値です。基本的な前処理ステップを通過したすべての遺伝子が保持されます。

```jldoctest
julia> result
19999×2 DataFrame
   Row │ gene_name  group1_vs_group2
       │ Any        Any
───────┼─────────────────────────────
     1 │ DE1        up
     2 │ DE2        up
     3 │ DE3        up
     4 │ DE4        up
     5 │ DE5        up
     6 │ DE6        up
   ⋮   │     ⋮             ⋮
 19995 │ EE19996    up
 19996 │ EE19997    up
 19997 │ EE19998    up
 19998 │ EE19999    up
 19999 │ EE20000    up
                   19988 rows omitted
```

#### 自分のDEG分析を実行する

分析の前に、2つの入力ファイルを準備する必要があります：メタデータファイルと発現マトリックス。`.rds`、`.csv`、`.txt`、`.tsv`、および`.RData`ファイルがサポートされています。

  * **メタデータファイル（必須）。**

メタデータファイルには少なくとも2つの列が含まれています。最初の列はサンプル名で、2番目の列はグループ情報です。現在は2つのグループのみがサポートされているため、2つ以上のグループを含めないでください。

メタデータの列名は`Name`と`Group`である必要があります。

メタデータファイルの例を参照してください：[fn_meta.txt](https://github.com/yanjer/RankCompV3.jl/blob/master/test/fn_meta.txt)。

  * **発現マトリックスファイル（必須）。**

最初の列は遺伝子名で、列ヘッダーは`Name`であり、残りの列は各細胞または各サンプルのプロファイルです。各列ヘッダーはメタデータファイルに表示されるサンプル名である必要があります。

発現マトリックスファイルの例を参照してください：[fn_expr.txt](https://github.com/yanjer/RankCompV3.jl/blob/master/test/fn_expr.txt)。

生のカウントまたは発現値の使用が推奨されます。他の値（例：FPKM、RPKM、TPM、log(counts)、log(normalized counts)）も使用できますが、正規化やバッチ効果の除去は必要でも推奨でもありません。

ファイルの準備が整ったら、以下のようにデフォルト設定でDEG分析を実行できます。

```jldoctest
julia> using RankCompV3
# 以下の他のパラメータのデフォルト値を使用します。パラメータを変更したい場合は、直接追加してください。
julia> reoa("/public/yanj/data/fn_expr.txt",
	"/public/yanj/data/fn_metadata.txt")
```

他のパラメータは、対応するキーワードに値を渡すことで設定できます。

```jldoctest
julia> reoa("/public/yanj/data/fn_expr.txt",
    	"/public/yanj/data/fn_metadata.txt",
    	expr_threshold = 0,
    	min_profiles = 0,
    	min_features = 0,
    	pval_reo = 0.01,
     	pval_deg = 1.0,
     	padj_deg = 0.05,
    	use_pseudobulk = 0,
    	use_hk_genes = "yes"
    	hk_file = "HK_genes_info.tsv",
    	gene_name_type = "ENSEMBL",
    	ref_gene_max = 3000,
    	ref_gene_min = 100
    	n_iter = 128,
    	n_conv = 5,
    	work_dir = "./",
    	use_testdata = "no")
```
