```
scaled_rand([rng], [T], dims...;
    scaling=0.1)
```

スケーリングによって定義された範囲内で一様に分布したランダム値を持つ行列を作成して返します。

# 引数

  * `rng`: ランダム数生成器。デフォルトはWeightInitializersの`Utils.default_rng()`です。
  * `T`: リザーバ行列の要素の型。デフォルトは`Float32`です。
  * `dims`: 行列の次元。`res_size x in_size`に従う必要があります。

# キーワード引数

  * `scaling`: 一様分布の範囲を定義するスケーリングファクター。行列の要素は範囲`[-scaling, scaling]`からランダムに選ばれます。デフォルトは`0.1`です。

# 例

```jldoctest
julia> res_input = scaled_rand(8, 3)
8×3 Matrix{Float32}:
 -0.0669356  -0.0292692  -0.0188943
  0.0159724   0.004071   -0.0737949
  0.026355   -0.0191563   0.0714962
 -0.0177412   0.0279123   0.0892906
 -0.0184405   0.0567368   0.0190222
  0.0944272   0.0679244   0.0148647
 -0.0799005  -0.0891089  -0.0444782
 -0.0970182   0.0934286   0.03553
```
