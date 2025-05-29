```julia
generateGraph_Helix2D!(; ...)
generateGraph_Helix2D!(
    numposes;
    posesperturn,
    graphinit,
    useMsgLikelihoods,
    solverParams,
    dfg,
    radius,
    spine_t,
    xr_t,
    yr_t,
    poseRegex,
    μ0,
    refKey,
    Qd,
    postpose_cb
)

```

ヘリックスパターンの一般化された標準グラフ生成関数。

ノート

  * ポーズは r"x\d+" に従ってラベル付けされていると仮定します。
  * 勾配（すなわち角度）計算は 1e-8 のオーダーです。
  * コールバック `spine_t(t)::Complex` を使用して、`t` の進行に沿ってヘリックスパターンが x, y でどのように移動するかを変更します。

      * 2D のヘリックスパターンの便利なジェネレーターのための関連ラッパー関数を参照してください。
      * 実数値の `xr_t(t)` と `yr_t(t)` は変更可能で（そして複素数値の `spine_t` を上書きします）。
  * 各新しいポーズの後に追加のユーザー機能のために `postpose_cb = (fg_, lastestpose) -> ...` を使用します。
  * 繰り返し呼び出すことでグラフを成長させることができますが、キーワードパラメータは呼び出し間で同一であると仮定されます。

参照: [`generateGraph_Helix2DSlew!`](@ref), [`generateGraph_Helix2DSpiral!`](@ref), [`generateGraph_Beehive!`](@ref)
