# まとめ関数: breed()

```
breed(cohort_A         ::Cohort,
      cohort_B         ::Cohort;
      n_gens           ::Int64=1,
      n_select         ::Int64=cohort_A.n + cohort_B.n,
      n_select_A   ::Int64=cohort_A.n,
      n_select_B ::Int64=cohort_B.n,
      select_all_gens  ::Bool=false,
      args...)

breed(cohort::Cohort, n_gens::Int64, args...) =
    breed(cohort, cohort, n_gens; args...)
```

### 引数

位置引数

  * `cohort_A` : 共通の交配親として扱われる `cohort` オブジェクト。オス/雄親であると仮定されます。
  * `cohort_B` : `cohort_A` と交配するために個体がサンプリングされる交配プールである `cohort` オブジェクト。メス/雌親であると仮定されます。

キーワード引数

  * `n_gens` : 何世代の交配選択が行われるかを指定する整数。
  * `n_select` : `ratio_malefemale` が `0` に設定されている場合に使用されます。`n_select` 個体が次世代の親として選択されます。
  * `n_select_A` : `ratio_malefemale` が `0` でない場合に使用されます。`n_select_A` が次世代の雄親として選択されます。
  * `n_select_B` : `ratio_malefemale` が `0` でない場合に使用されます。`n_select_B` が次世代の雌親として選択されます。
  * `select_all_gens` : デフォルトは "false" で、親は次世代プールの選択に含まれません。すべての世代からの個体を考慮する場合は `select_all_gens` を "true" に設定します。

### 出力

デフォルトでは、2つの `cohort` オブジェクトが返されます。最初の `cohort` は雄の子孫であると仮定され、もう一方の `cohort` は雌の子孫です。2つのコホートのサイズは `raiot_malefemale` の比率に従います。`ratio_malefemale` が `0` に設定されている場合、1つの `cohort` のみが返されます。

### 例

`10` の雄親を持ち、各雄親を `5` の雌親と交配させて `5` 世代を行うことができます。各世代で、ランダムに `10` の雄の子孫を雄親として選択し、すべての雌の子孫を雌親として次世代に使用します。このような繁殖スキームを以下のように導出できます。

```jldoctest
julia> args  = Dict(# 交配引数
                    :nA               => 10,
                    :nB_per_A         => 5,
                    :n_per_mate       => 2,
                    :ratio_malefemale => 1.0,
                    # 選択引数
                    :is_random        => true,
                    # 繁殖引数
                    :n_gens           => 5,
                    :nA_select        => 10,
                    :select_all_gens  => true)
```

10 の雄親と 50 の雌親を創始者としてシミュレートします。

```jldoctest
julia> sires = Founders(10)
julia> dams  = Founders(50)
```

定義された引数に基づいてコホートを繁殖させます。

```jldoctest
julia> sires, dams = breed(sires, dams; args...)
[ Info: Gen 0 -> Mean of BVs: [1.665 2.745], Variance of BVs: [1.008 0.479]
[ Info: Gen 1 -> Mean of BVs: [1.719 2.715], Variance of BVs: [0.96 0.546]
[ Info: Gen 2 -> Mean of BVs: [1.754 2.777], Variance of BVs: [0.936 0.724]
[ Info: Gen 3 -> Mean of BVs: [1.766 2.796], Variance of BVs: [0.927 0.775]
[ Info: Gen 4 -> Mean of BVs: [1.773 2.771], Variance of BVs: [0.951 0.781]
[ Info: Gen 5 -> Mean of BVs: [1.813 2.751], Variance of BVs: [0.952 0.804]
([ Info: Cohort (60 individuals)
[ Info: 
[ Info: Mean of breeding values: 
[ Info: [1.855 2.593]
[ Info: 
[ Info: Variance of breeding values: 
[ Info: [0.884 0.697]
, [ Info: Cohort (300 individuals)
[ Info: 
[ Info: Mean of breeding values: 
[ Info: [1.805 2.782]
[ Info: 
[ Info: Variance of breeding values: 
[ Info: [0.969 0.822]
```

結果は次の交配選択の反復に相当します。

```jldoctest
julia> for _ in 1:5
            males, females = mate(sires, dams, args...)
            sires         += select(males, n_sires, args...)
            dams          += females
       end
```
