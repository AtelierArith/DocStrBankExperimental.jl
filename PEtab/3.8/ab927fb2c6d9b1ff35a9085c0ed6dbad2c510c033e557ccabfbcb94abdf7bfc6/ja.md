```
solve_all_conditions(x, prob::PEtabODEProblem, solver; kwargs)
```

`prob`のODEモデルを、提供されたODEソルバーで全てのシミュレーション条件に対して解きます。

`x`は、`prob`が期待する順序でパラメータを持つ`Vector`または`ComponentArray`である必要があります（[`get_x`](@ref)を参照）。

# キーワード引数

  * `abstol=1e-8`: ODEソルバーの絶対許容誤差。
  * `reltol=1e-8`: ODEソルバーの相対許容誤差。
  * `maxiters=1e4`: ODEソルバーの最大反復回数。
  * `ntimepoints_save=0`: 各条件に対してODE解を保存する時間点の数。0の値は、解がソルバーのデフォルトの時間点で保存されることを意味します。
  * `save_observed_t=false`: trueに設定すると、このオプションは`ntimepoints_save`を上書きし、測定データが利用可能な時間点でのみODE解を保存します。

# 戻り値

  * `odesols`: 各シミュレーション条件の`ODESolution`を含む辞書。
