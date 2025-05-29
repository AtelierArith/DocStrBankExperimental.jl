# クイックスタート

`markers` と `chromosomes` の数を割り当てることで簡単にセットアップできます。

```
build_genome(;n_loci ::Int64=-1,
              n_chr    ::Int64=10,
              species  ::String="none",
              args...)
```

## 引数

  * `n_loci` : 各染色体のシミュレーションされたマーカーの数
  * `n_chr`: 100セントモルの長さを持つシミュレーションされた染色体の数
  * `species` : 事前にロードされた連鎖地図によって遺伝的位置（モーガン）を推定します。利用可能な種は: ["cattle", and "pig"]

## 例

```jldoctest
julia> build_genome(n_chr  = 2,
                    n_loci = 10000)

[ Info: --------- ゲノムサマリー ---------
[ Info: 染色体の数  : 2
[ Info:
[ Info: 染色体の長さ (cM): 200.0
[ Info: [100.0, 100.0]
[ Info:
[ Info: ロキの数        : 20000
[ Info: [10000, 10000]
[ Info:
[ Info: ジェノタイピングエラー      : 0.0
[ Info: 突然変異率         : 0.0
[ Info:
```

# ファイルまたはDataFrameによるゲノムの定義

フォーマットされたデータフレームまたはファイルへのパスを提供することでゲノムを定義します。

```
build_genome(dt      ::DataFrame;
             species ::String="none",
             args...)

build_genome(filename::String;
             species ::String="none",
             args...)
```

## 引数

  * `dt` : 必要な列 `chr` と `cM` を持つ `DataFrame`、または推定のために `species` が提供されている場合は `chr` と `bp`。
  * `filename` : ゲノム情報を含むファイルへのファイルパス。
  * `species` : 事前にロードされた連鎖地図によって遺伝的位置（モーガン）を調整します。利用可能な種は: ["cattle", and "pig"]

## `DataFrame` の例

```
4×7 DataFrame
 Row │ id      chr    bp       cM       MAF      eff_1    eff_2
     │ String  Int64  Int64    Float64  Float64  Float64  Float64
─────┼────────────────────────────────────────────────────────────
   1 │ snp_1       1  1818249     50.8      0.5      0.1      0.0
   2 │ snp_2       1  6557697     80.3      0.5      0.0      0.0
   3 │ snp_3       2  2298800     39.2      0.5      0.2      0.0
   4 │ snp_4       2  5015698     66.3      0.5      0.0      0.5
```

## 例

ファイルパスによる

```jldoctest
julia> build_genome("path/map.csv";
                    rate_mutation=0.005, rate_error=0.01)
```

またはデータフレームによる

```jldoctest
julia> using DataFrames
julia> data = CSV.read("path/map.csv", DataFrame)
julia> build_genome(data;
                    rate_mutation=0.005, rate_error=0.01)

[ Info: --------- ゲノムサマリー ---------
[ Info: 染色体の数  : 2
[ Info:
[ Info: 染色体の長さ (cM): 146.6
[ Info: [80.3, 66.3]
[ Info:
[ Info: ロキの数        : 4
[ Info: [2, 2]
[ Info:
[ Info: ジェノタイピングエラー      : 0.01
[ Info: 突然変異率         : 0.005
[ Info:
```

牛のゲノムを参照として使用して遺伝的位置を推定します

```jldoctest
julia> build_genome("path/map.csv"; species="cattle")

[ Info: Arias,J.A. et al. (2009) A high density linkage map of the bovine genome. BMC Genetics, 10, 18.
[ Info: 参照ゲノム : Btau 4.0
[ Info: SNPチップ         : Affymetrix GeneChip Bovine Mapping 10K SNP kit

┌ Warning: 提供された遺伝的距離は、事前にロードされた連鎖地図から推定されたものに置き換えられます
└ @ XSim ~/Dropbox/projects/XSim/src/objects/global.jl:118
[ Info: --------- ゲノムサマリー ---------
[ Info: 染色体の数  : 2
[ Info:
[ Info: 染色体の長さ (cM): 16.8
[ Info: [15.1, 1.7]
[ Info:
[ Info: ロキの数        : 4
[ Info: [2, 2]
[ Info:
[ Info: ジェノタイピングエラー      : 0.0
[ Info: 突然変異率         : 0.0
[ Info:

```

# 明示的な定義

各ロキの遺伝情報を明示的に提供することでゲノムを定義します。

```
build_genome(chromosome    ::Array{Int64,   1},
             bp            ::Array{Int64,   1},
             cM            ::Array{Float64, 1},
             maf           ::Array{Float64, 1};
             rate_mutation ::Float64=0.0,
             rate_error    ::Float64=0.0)
```

## 引数

  * `chromosome` : 染色体コード
  * `bp` : 物理的位置
  * `cM` : 遺伝的位置
  * `maf` : マイナーアレル頻度
  * `rate_mutation` : 突然変異率
  * `rate_error` : ジェノタイピングのエラー率

## 例

```jldoctest
julia> ch  = [1,    1,     2,    2,    2]
julia> bp  = [130,  205,   186,  503,  780]
julia> cM  = [85.7, 149.1, 37.4, 83.6, 134.3]
julia> maf = [0.5,  0.5,   0.5,  0.5,  0.5]
julia> build_genome(ch, bp, cM, maf)

[ Info: --------- ゲノムサマリー ---------
[ Info: 染色体の数  : 2
[ Info:
[ Info: 染色体の長さ (cM): 283.4
[ Info: [149.1, 134.3]
[ Info:
[ Info: ロキの数        : 5
[ Info: [2, 3]
[ Info:
[ Info: ジェノタイピングエラー      : 0.0
[ Info: 突然変異率         : 0.0
[ Info:
```
