# 遺伝的評価

```
genetic_evaluation(cohort         ::Cohort,
                   phenotypes     ::DataFrame=DataFrame();
                   model_equation ::String="",
                   covariates     ::String="",
                   random_iid     ::String="",
                   random_str     ::String="",
                   methods        ::String="GBLUP",
                   add_genotypes  ::Bool=true,
                   idx_missing_p  ::Any=[],
                   return_out     ::Bool=false,
                   args...)
```

### 引数

  * `cohort` : 評価された `cohort`。
  * `phenotypes` : `id`、特性、および他の研究された要因の列を持つ `dataframe`。
  * `h2` : デフォルトは0.5。`phenotype`が提供されていない場合のコホート表現型をシミュレートするための遺伝率。
  * `ve` : デフォルトは1。`phenotype`が提供されていない場合のコホート表現型をシミュレートするための残差分散。
  * `model_equation` : デフォルトは "y ~ intercept"。育種値をフィットさせるための方程式。
  * `covariates` : `phenotypes`内の項を連続因子として指定します。`model_equation`にも含める必要があります。
  * `random_iid` : `phenotypes`内の項をランダム効果（i.i.d.）として指定します。`model_equation`にも含める必要があります。
  * `random_str` : `phenotypes`内の項をランダム効果（系譜）として指定します。`model_equation`にも含める必要があります。
  * `methods` : デフォルトは "GBLUP"。遺伝的評価に使用されるモデル/方法を定義します。
  * `add_genotypes` : デフォルトは `true`。方程式に遺伝子型が含まれます。
  * `idx_missing_p` : 表現型がない個体を割り当てるベクトル。
  * `return_out` : デフォルトは `false`。`true`に設定すると、完全な `JWAS` 出力が返されます。

### 出力

`return_out = false` の場合、育種値を含む `n` by `t` 行列が返されます。ここで、`n` は個体の数、`t` は評価された特性の数です。`return_out = true` の場合、完全な `JWAS` 出力が返されます。

### `phenotypes` データフレームの例

```jldoctest
 Row │ ID           y1              y2               factor_1  factor_2
     │ String       Float64?        Float64?         Int64     Int64
─────┼─────────────────────────────────────────────────────────────
   1 │ 1             0.88976        -0.0798048         1         1
   2 │ 2            -0.783203        0.988616          1         1
   3 │ 3             missing         missing           1         1
   4 │ 4             missing         missing           1         1
   5 │ 5             missing         missing           1         1
   6 │ 6             missing         missing           1         2
   7 │ 7             missing         missing           1         2
   8 │ 8            -1.76058         0.277289          1         2
   9 │ 9             0.938871        2.57784           1         2
  10 │ 10            0.37026         3.15993           1         2
  11 │ 11           -1.91869         0.0935064         2         3
  12 │ 12           -0.89847         1.8987            2         3
  13 │ 13            1.69663        -0.949513          2         3
  14 │ 14            3.48862         0.654378          2         3
  15 │ 15            1.39615         1.80355           2         3
  16 │ 16            2.31685         2.13446           2         4
  17 │ 17           -3.81017         0.0186156         2         4
  18 │ 18           -1.71216        -0.0976809         2         4
  19 │ 19            1.80917         1.34104           2         4
  20 │ 20           -0.504771        3.22665           2         4
```

### 例

デモの `genome` と `phenome` を使用します。20人の個体を持つ `cohort` がシミュレートされます。

```jldoctest
julia> build_demo()
[ Info: --------- Genome Summary ---------
[ Info: Number of Chromosome  : 10
[ Info:
[ Info: Chromosome Length (cM):
[ Info: [150.0, 150.0, 150.0, 150.0, 150.0, 150.0, 150.0, 150.0, 150.0, 150.0]
[ Info:
[ Info: Number of Loci        : 1000
[ Info: [100, 100, 100, 100, 100, 100, 100, 100, 100, 100]
[ Info:
[ Info: Genotyping Error      : 0.0
[ Info: Mutation Rate         : 0.0
[ Info:
[ Info: --------- Phenome Summary ---------
[ Info: Number of Traits      : 2
[ Info: Heritability (h2)     : [0.5, 0.5]
┌ Info:
│   Genetic_Variance =
│    2×2 Array{Float64,2}:
│     1.0  0.0
└     0.0  1.0
┌ Info:
│   Residual_Variance =
│    2×2 Array{Float64,2}:
│     1.0  0.0
└     0.0  1.0
[ Info: Number of QTLs        : [3 8]

julia> cohort = Cohort(20)
[ Info: Cohort (20 individuals)
[ Info:
[ Info: Mean of breeding values:
[ Info: [-0.862 -0.913]
[ Info:
[ Info: Variance of breeding values:
[ Info: [0.814 1.448]
```

─────────────────────────────────────────────────────────

#### 基本的な使用法

デフォルトでは、引数を提供せずにGBLUPが実行されます。

```jldoctest
julia> out = genetic_evaluation(cohort)
20×2 Array{Float64,2}:
  42.2908     -5.89224
   6.38041    -4.5895
  19.5065    -57.4513
  24.05      -84.5086
  11.5925     45.5247
 -11.5926     -1.91879
 -29.2152    -35.5977
  -1.92563    63.8841
  19.8686     76.2722
  22.6728     45.5179
 -58.2754     42.5953
  28.556     -21.0314
  11.5918     25.1126
  -0.517653   -0.237724
 -11.4712    -47.3073
 -10.9575     -3.58754
 -11.7835     -9.62802
 -17.7895    -22.0821
 -39.5114     -3.46026
   6.53008    -1.61416
```

育種値 `out` は、選択の基準として直接使用できます。

```jldoctest
julia> select(cohort, 5, out)
[ Info: --------- Selection Summary ---------
[ Info: Select 5 individuals out of 20 individuals
[ Info: Selection differential (P): [0.783 1.192]
[ Info: Selection response     (G): [0.344 1.063]
┌ Info: 
│   Residual_Variance =
│    2×2 Array{Float64,2}:
│     1.0  0.0
└     0.0  1.0
[ Info: --------- Offsprings Summary ---------
[ Info: Cohort (5 individuals)
[ Info:
[ Info: Mean of breeding values:
[ Info: [-0.552 0.367]
[ Info:
[ Info: Variance of breeding values:
[ Info: [0.181 0.539]
```

評価の条件は、`h2` または `ve` によってさらに定義できます。

```jldoctest
julia> out = genetic_evaluation(cohort, ve = [1  0.5
                                             0.5  1])
```

`return_out = true` に設定すると、完全な `JWAS` 出力を取得できます。

```jldoctest
julia> out = genetic_evaluation(cohort, return_out = true)
Dict{Any,Any} with 7 entries:
  "EBV_y2"              => 20×3 DataFrame…
  "EBV_y1"              => 20×3 DataFrame…
  "heritability"        => 2×3 DataFrame…
  "location parameters" => 2×5 DataFrame…
  "residual variance"   => 4×3 DataFrame…
  "marker effects geno" => 40×5 DataFrame…
  "genetic_variance"    => 4×3 DataFrame…
```

─────────────────────────────────────────────────────────

#### カスタマイズされた表現型と要因

JWAS互換のデータフレームを取得します。

```jldoctest
dt_p = get_phenotypes(cohort, "JWAS")
```

表現型がない個体を割り当てます。

```jldoctest
julia> idx = 3:6
julia> allowmissing!(dt_p);
julia> dt_p[idx, 2:end] .= missing;
julia> first(dt_p, 10)
10×3 DataFrame
 Row │ ID            y1               y2
     │ String?       Float64?         Float64?
─────┼──────────────────────────────────────────
   1 │ 1             -0.0933375       -0.882781
   2 │ 2             -1.50748         -2.12898
   3 │ 3              missing          missing
   4 │ 4              missing          missing
   5 │ 5              missing          missing
   6 │ 6              missing          missing
   7 │ 7             -0.431361        -0.624666
   8 │ 8             -1.17867          0.415607
   9 │ 9              0.266733         1.02123
  10 │ 10            -1.15588          0.737982
```

評価のためにカスタマイズされた表現型を提供します。

```jldoctest
julia> out = genetic_evaluation(dams, dt_p)
```

これは、欠損表現型のために `idx_missing_p = 3:6` を設定するのと同等です。

```jldoctest
julia> out = genetic_evaluation(dams, dt_p, idx_missing_p = 3:6)
マーカーIDは1,2,...,#markersに設定されています
個体IDは1,2,...,#observationsに設定されています
遺伝子型情報:
#markers: 1000; #individuals: 20
結果を保存するためのフォルダが作成されました。
遺伝子型をチェックしています...
表現型をチェックしています...
表現型データの最初の列に個体ID（文字列）が提供されています。
16人の個体の表現型が分析に使用されます。これらの個体IDはファイル IDs_for_individuals_with_phenotypes.txt に保存されます。
```

`factor_1` と `factor_2` をそれぞれ固定効果とランダム効果としてシミュレートできます。そして、`y1` をフィットさせるために `factor_1` と `factor_2` の両方を使用し、`y2` をフィットさせるために `factor_1` のみを使用します。

```jldoctest
julia> dt_p[:, "factor_1"] = [i for i in 1:4 for j in 1:5];
julia> dt_p[:, "factor_2"] = [i for i in 1:2 for j in 1:10];
julia> out = genetic_evaluation(cohort, dt_p,
                model_equation="y1 = intercept + factor_1 + factor_2
                                y2 = intercept + factor_1",
                random_iid="factor_2",
                return_out=true)

factor_2はモデル方程式2に見つかりません。
マーカーIDは1,2,...,#markersに設定されています
個体IDは1,2,...,#observationsに設定されています
遺伝子型情報:
#markers: 1000; #individuals: 20
結果を保存するためのフォルダが作成されました。
遺伝子型をチェックしています...
表現型をチェックしています...
表現型データの最初の列に個体ID（文字列）が提供されています。
16人の個体の表現型が分析に使用されます。これらの個体IDはファイル IDs_for_individuals_with_phenotypes.txt に保存されます。
ランダム効果分散のための事前情報が提供されておらず、データから生成されます。

Pi (Π) は提供されていません。
Pi (Π) は、すべてのマーカーがすべての特性に影響を与えると仮定して生成されます。

線形混合モデルがモデル方程式を使用して構築されました：

y1 = intercept + factor_1 + factor_2
y2 = intercept + factor_1

モデル情報：

項            C/F          F/R            nLevels
intercept       factor       fixed                1
factor_1        factor       fixed                4
factor_2        factor       random               2

MCMC情報：

chain_length                                    100
burnin                                            0
starting_value                                 true
printout_frequency                              101
output_samples_frequency                          1
constraint                                    false
missing_phenotypes                             true
update_priors_frequency                           0
seed                                          false

ハイパーパラメータ情報：

ランダム効果分散 (y1:factor_2):
 0.45
残差分散：
 1.0f0  0.0f0
 0.0f0  1.0f0

ゲノム情報：

完全なゲノムデータ（すなわち、単一ステップ分析ではない）

ゲノムカテゴリ                               geno
方法                                        GBLUP
遺伝的分散（ゲノム）：
 1.0  0.0
 0.0  1.0
estimateScale                                 false

ハイパーパラメータの自由度：

残差分散：                           6.000
ランダム効果分散：                      5.000
マーカー効果分散：                      6.000

使用中のJuliaとプラットフォームのバージョン：

Julia Version 1.5.4
Commit 69fcb5745b (2021-03-11 19:13 UTC)
プラットフォーム情報：
  OS: macOS (x86_64-apple-darwin18.7.0)
  CPU: Intel(R) Core(TM) i7-9750H CPU @ 2.60GHz
  WORD_SIZE: 64
  LIBM: libopenlibm
  LLVM: libLLVM-9.0.1 (ORCJIT, skylake)
環境：
  JULIA_EDITOR = code
  JULIA_NUM_THREADS =

分析が完了しました。結果は返された変数とテキストファイルに保存されます。MCMCサンプルはテキストファイルに保存されます。

Dict{Any,Any} with 7 entries:
  "EBV_y2"              => 20×3 DataFrame…
  "EBV_y1"              => 20×3 DataFrame…
  "heritability"        => 2×3 DataFrame…
  "location parameters" => 12×5 DataFrame…
  "residual variance"   => 4×3 DataFrame…
  "marker effects geno" => 32×5 DataFrame…
  "genetic_variance"    => 4×3 DataFrame…
```
