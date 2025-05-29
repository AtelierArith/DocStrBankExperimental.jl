```
ancestralreconstruction(obj::PhyloNetworkLinearModel[, X_n::Matrix])
```

ネットワーク上の祖先の特性再構築を見つけるための関数で、[`phylolm`](@ref)関数によってフィットされたオブジェクトが与えられます。デフォルトでは、関数は回帰変数が単なる切片であると仮定します。すべての祖先状態の回帰変数の値が知られている場合、それをX*nに入力できます。X*nは、使用された予測子の数と同じ数の列を持ち、未知のノードまたはチップの数と同じ数の行を持つ行列です。

[`ReconstructedStates`](@ref)型のオブジェクトを返します。

# 例

```jldoctest; filter = [r" PhyloTraits .*:\d+", ]
julia> using DataFrames, CSV # データファイルを読み込むため

julia> phy = readnewick(joinpath(dirname(pathof(PhyloTraits)), "..", "examples", "carnivores_tree.txt"));

julia> dat = CSV.read(joinpath(dirname(pathof(PhyloTraits)), "..", "examples", "carnivores_trait.txt"), DataFrame);

julia> using StatsModels # 統計モデルの式のため

julia> fitBM = phylolm(@formula(trait ~ 1), dat, phy);

julia> ancStates = ancestralreconstruction(fitBM) # 分散が不明なため警告が表示されるはずです。
┌ Warning: これらの予測区間は祖先の値に不確実性を示しています、
│ 推定された進化の分散率が正しいと仮定しています。
│ この分散率の推定における追加の不確実性は
│ 無視されるため、予測区間は大きくなるべきです。
└ @ PhyloTraits ~/build/JuliaPhylo/PhyloTraits.jl/src/traits_continuous.jl:2601
ReconstructedStates:
───────────────────────────────────────────────
  ノードインデックス      予測値        最小値  最大値 (95%)
───────────────────────────────────────────────
        -5.0   1.32139   -0.33824      2.98102
        -8.0   1.03258   -0.589695     2.65485
        -7.0   1.41575   -0.140705     2.97221
        -6.0   1.39417   -0.107433     2.89577
        -4.0   1.39961   -0.102501     2.90171
        -3.0   1.51341   -0.220523     3.24733
       -13.0   5.3192     3.92279      6.71561
       -12.0   4.51176    2.89222      6.13131
       -16.0   1.50947   -0.0186118    3.03755
       -15.0   1.67425    0.196069     3.15242
       -14.0   1.80309    0.309992     3.29618
       -11.0   2.7351     1.17608      4.29412
       -10.0   2.73217    1.12361      4.34073
        -9.0   2.41132    0.603932     4.21871
        -2.0   2.04138   -0.0340955    4.11686
        14.0   1.64289    1.64289      1.64289
         8.0   1.67724    1.67724      1.67724
         5.0   0.331568   0.331568     0.331568
         2.0   2.27395    2.27395      2.27395
         4.0   0.275237   0.275237     0.275237
         6.0   3.39094    3.39094      3.39094
        13.0   0.355799   0.355799     0.355799
        15.0   0.542565   0.542565     0.542565
         7.0   0.773436   0.773436     0.773436
        10.0   6.94985    6.94985      6.94985
        11.0   4.78323    4.78323      4.78323
        12.0   5.33016    5.33016      5.33016
         1.0  -0.122604  -0.122604    -0.122604
        16.0   0.73989    0.73989      0.73989
         9.0   4.84236    4.84236      4.84236
         3.0   1.0695     1.0695       1.0695
───────────────────────────────────────────────

julia> using StatsBase # 予測関数のため

julia> predict(ancStates)
31×2 DataFrame
 Row │ nodenumber  prediction 
     │ Int64       Float64    
─────┼────────────────────────
   1 │         -5    1.32139
   2 │         -8    1.03258
   3 │         -7    1.41575
   4 │         -6    1.39417
   5 │         -4    1.39961
   6 │         -3    1.51341
   7 │        -13    5.3192
   8 │        -12    4.51176
  ⋮  │     ⋮           ⋮
  25 │         10    6.94985
  26 │         11    4.78323
  27 │         12    5.33016
  28 │          1   -0.122604
  29 │         16    0.73989
  30 │          9    4.84236
  31 │          3    1.0695
               16 rows omitted

julia> predict(ancStates, interval = :prediction)
31×4 DataFrame
 Row │ nodenumber  prediction  lower       upper     
     │ Int64       Float64     Float64     Float64   
─────┼───────────────────────────────────────────────
   1 │         -5    1.32139   -0.33824     2.98102
   2 │         -8    1.03258   -0.589695    2.65485
   3 │         -7    1.41575   -0.140705    2.97221
   4 │         -6    1.39417   -0.107433    2.89577
   5 │         -4    1.39961   -0.102501    2.90171
   6 │         -3    1.51341   -0.220523    3.24733
   7 │        -13    5.3192     3.92279     6.71561
   8 │        -12    4.51176    2.89222     6.13131
  ⋮  │     ⋮           ⋮           ⋮           ⋮
  25 │         10    6.94985    6.94985     6.94985
  26 │         11    4.78323    4.78323     4.78323
  27 │         12    5.33016    5.33016     5.33016
  28 │          1   -0.122604  -0.122604   -0.122604
  29 │         16    0.73989    0.73989     0.73989
  30 │          9    4.84236    4.84236     4.84236
  31 │          3    1.0695     1.0695      1.0695
                                      16 rows omitted

julia> using PhyloPlots # 次: 木の上に祖先状態をプロット

julia> plot(phy, nodelabel = predict(ancStates));

julia> pred = predict(ancStates, interval = :prediction, text = true);

julia> plot(phy, nodelabel = pred[!,[:nodenumber,:interval]]);

julia> allowmissing!(dat, :trait);

julia> dat[[2, 5], :trait] .= missing; # モデルにフィットするために欠損値を許可

julia> fitBM = phylolm(@formula(trait ~ 1), dat, phy);

julia> ancStates = ancestralreconstruction(fitBM);
┌ Warning: これらの予測区間は祖先の値に不確実性を示しています、
│ 推定された進化の分散率が正しいと仮定しています。
│ この分散率の推定における追加の不確実性は
│ 無視されるため、予測区間は大きくなるべきです。
└ @ PhyloTraits ~/build/JuliaPhylo/PhyloTraits.jl/src/traits_continuous.jl:2601

julia> first(predict(ancStates), 3) # 最初の3ノードのみを見る
3×2 DataFrame
 Row │ nodenumber  prediction 
     │ Int64       Float64    
─────┼────────────────────────
   1 │         -5     1.42724
   2 │         -8     1.35185
   3 │         -7     1.61993

julia> first(predict(ancStates, interval=:prediction), 3)
3×4 DataFrame
 Row │ nodenumber  prediction  lower      upper   
     │ Int64       Float64     Float64    Float64 
─────┼────────────────────────────────────────────
   1 │         -5     1.42724  -0.373749  3.22824
   2 │         -8     1.35185  -0.698432  3.40214
   3 │         -7     1.61993  -0.17179   3.41165

julia> plot(phy, nodelabel = predict(ancStates, text=true));

julia> pred = predict(ancStates, interval = :prediction, text = true);

julia> plot(phy, nodelabel = pred[!,[:nodenumber,:interval]]);
```
