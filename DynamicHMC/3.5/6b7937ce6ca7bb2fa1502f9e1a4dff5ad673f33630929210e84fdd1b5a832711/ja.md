```julia
struct InitialStepsizeSearch
```

初期ステップサイズのための探索アルゴリズムのパラメータ。

このアルゴリズムは、局所的な対数受容比 $A(ϵ)$ が `params.log_threshold` に近くなるように初期ステップサイズ $ϵ$ を見つけます。

  * `initial_ϵ`: 探索が開始されるステップサイズ。
  * `log_threshold`: 超える必要がある閾値の対数。
  * `maxiter_crossing`: 閾値を超えるための最大反復回数。

!!! NOTE

```
このアルゴリズムはHoffmanとGelman（2014）からのもので、デフォルトの閾値はStanの後の実践に従って`0.8`に修正されています。
```
