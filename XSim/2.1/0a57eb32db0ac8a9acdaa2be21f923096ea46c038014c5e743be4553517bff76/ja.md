# 交配関数

```
mate(cohort_A         ::Cohort,
     cohort_B         ::Cohort;
     nA               ::Int64=cohort_A.n,
     nB_per_A         ::Int64=1,
     n_per_mate       ::Int64=1,
     replace_A        ::Bool =false,
     replace_B        ::Bool =false,
     ratio_malefemale ::Union{Float64, Int64}=0,
     scheme           ::String ="none",
     args...)

mate(cohort::Cohort; args...) =  mate(cohort, cohort; args...)
```

## 引数

位置引数

  * `cohort_A` : 共通の交配親として扱われる `cohort` オブジェクト。
  * `cohort_B` : `cohort_A` と交配するために個体がサンプリングされる交配プールである `cohort` オブジェクト。

キーワード引数

  * `nA` : `nA` 個体が `cohort_A` からサンプリングされ、共通の親として扱われる。
  * `nB_per_A` : `cohort_B` からサンプリングされた `nB_per_A` 個体が `cohort_A` の各個体と交配する。
  * `n_per_mate` : 各交配親のペアから `n_per_mate` の子孫が再生産される。
  * `replace_A` : `cohort_A` でのサンプリングが置き換え可能かどうか。
  * `replace_B` : `cohort_B` でのサンプリングが置き換え可能かどうか。
  * `ratio_malefemale` : デフォルトでは、オスとメスの子孫を持つ2つのコホートが返される。`ratio_malefemale` はオスとメスの子孫の比率を定義する。`ratio_malefemale=0` の場合、1つのコホートのみが返される。
  * `scheme` : 利用可能なオプションは ["random", "diallel cross", "selfing", "DH"]。詳細については例を参照。

## 出力

デフォルトでは、2つの `cohort` オブジェクトが返される。最初の `cohort` はオスの子孫と仮定され、もう1つの `cohort` はメスの子孫である。2つのコホートのサイズは `raiot_malefemale` の比率に従う。`ratio_malefemale` が `0` に設定されている場合、1つの `cohort` のみが返される。

## 例

### ランダム交配（デフォルト）

コホートの初期化

```jldoctest
julia> cohort_A = Cohort(5)
julia> cohort_B = Cohort(10)
```

交配イベントの定義

```jldoctest
julia> args = Dict(:nA               => cohort_A.n,
                   :nB_per_A         => 1,
                   :replace_A        => false,
                   :replace_B        => false,
                   :n_per_mate       => 1)
julia> progenies = mate(cohort_A, cohort_B; args...)

# 同等
julia> progenies = mate(cohort_A, cohort_B)

# 同等
julia> progenies = mate(cohort_A, cohort_B; scheme="random")

# 同等
julia> progenies = cohort_A * cohort_B
```

交配が期待通りに行われているかを確認するために系譜をチェックします。

```jldoctest
julia> get_pedigree(progenies)
5×3 LinearAlgebra.Adjoint{Int64,Array{Int64,2}}:
 19  1   8
 16  2   6
 17  3  10
 20  4  15
 18  5  14
```

### ダイレル交配

コホートの初期化

```jldoctest
julia> cohort_A = Cohort(2)
julia> cohort_B = Cohort(5)
```

交配イベントの定義

```jldoctest
julia> args = Dict(:nA              => sires.n,
                   :nB_per_A        => dams.n,
                   :replace_A       => false,
                   :replace_B       => false,
                   :n_per_mate      => 1,
                   :ratio_malefemale=> 1)
julia> male, female = mate(cohort_A, cohort_B; args...)

# 同等
julia> male, female = mate(cohort_A, cohort_B; scheme="diallel cross")
```

交配が期待通りに行われているかを確認するために系譜をチェックします。

```jldoctest
julia> get_pedigree(male + female)
10×3 LinearAlgebra.Adjoint{Int64,Array{Int64,2}}:
 12  2  7
 10  2  6
 11  2  4
 14  1  3
 15  1  5
  9  2  5
 13  1  6
 17  1  4
  8  2  3
 16  1  7
```

### 自家受精

コホートの初期化

```jldoctest
julia> parents = Cohort(5)
```

自家受精スキームでは、1つの `cohort` のみが必要です。

```jldoctest
julia> args = Dict(:nA          => 3,
                   :replace_A   => false,
                   :n_per_mate  => 5,
                   :scheme      => "selfing")
julia> progenies = mate(parents; args...)
```

交配の挙動を確認するために系譜を検査します。

```jldoctest
julia> get_pedigree(progenies)
15×3 LinearAlgebra.Adjoint{Int64,Array{Int64,2}}:
  6  4  4
  7  4  4
  8  4  4
  9  4  4
 10  4  4
 11  1  1
 12  1  1
 13  1  1
 14  1  1
 15  1  1
 16  5  5
 17  5  5
 18  5  5
 19  5  5
 20  5  5
```
