```
lrtest(mods::StatisticalModel...; atol::Real=0.0)
```

`mods...`の各連続ペアの統計モデルに対して、最初のモデルが次のモデルよりも有意に適合しているかどうかを判断するために、尤度比検定を実行します。

前のモデルからの自由度（DOF）、DOFの差、対数尤度、偏差、カイ二乗統計量（すなわち、対数尤度の差の2倍の絶対値）、および2つのモデル間の比較のp値を含むテーブルが返されます。

オプションのキーワード引数`atol`は、モデルがネストされているかどうかをテストする際の数値的許容誤差を制御します。

# 例

2つ以上の処置がある結果に対する効果を比較したいとします。私たちの帰無仮説は、`Result ~ 1`が`Result ~ 1 + Treatment`と同様にデータに適合しているというものです。

```jldoctest
julia> using DataFrames, GLM

julia> dat = DataFrame(Result=[1, 0, 1, 1, 1, 0, 0, 0, 1, 0, 1, 1],
                       Treatment=[1, 1, 1, 2, 2, 2, 1, 1, 1, 2, 2, 2],
                       Other=string.([1, 1, 2, 1, 2, 1, 3, 1, 1, 2, 2, 1]));

julia> nullmodel = glm(@formula(Result ~ 1), dat, Binomial(), LogitLink());

julia> model = glm(@formula(Result ~ 1 + Treatment), dat, Binomial(), LogitLink());

julia> bigmodel = glm(@formula(Result ~ 1 + Treatment + Other), dat, Binomial(), LogitLink());

julia> lrtest(nullmodel, model, bigmodel)
尤度比検定: 12の観測値に対して3つのモデルが適合しました
────────────────────────────────────────────────────
     DOF  ΔDOF   LogLik  Deviance   Chisq  p(>Chisq)
────────────────────────────────────────────────────
[1]    1        -8.1503   16.3006
[2]    2     1  -7.9780   15.9559  0.3447     0.5571
[3]    4     2  -7.0286   14.0571  1.8988     0.3870
────────────────────────────────────────────────────

julia> lrtest(bigmodel, model, nullmodel)
尤度比検定: 12の観測値に対して3つのモデルが適合しました
────────────────────────────────────────────────────
     DOF  ΔDOF   LogLik  Deviance   Chisq  p(>Chisq)
────────────────────────────────────────────────────
[1]    4        -7.0286   14.0571
[2]    2    -2  -7.9780   15.9559  1.8988     0.3870
[3]    1    -1  -8.1503   16.3006  0.3447     0.5571
────────────────────────────────────────────────────
```
