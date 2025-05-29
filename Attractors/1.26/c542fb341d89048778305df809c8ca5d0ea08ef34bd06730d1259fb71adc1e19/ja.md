```
animate_attractors_continuation(
    ds::DynamicalSystem, attractors_cont, fractions_cont, pcurve;
    kwargs...
)
```

見つかったシステムアトラクタとそれに対応するバシンの割合が、システムパラメータの増加に伴ってどのように変化するかをアニメーションで示します。この関数は、[`global_continuation`](@ref) 関数の入力と出力を動画出力に統合します。

入力ダイナミカルシステム `ds` は、見つかったアトラクタからサンプリングされた初期条件を進化させるために使用され、アトラクタがより良く視覚化されます。`attractors_cont, fractions_cont` は [`global_continuation`](@ref) の出力であり、`ds, pcurve` は [`global_continuation`](@ref) への入力です。

## キーワード引数

  * `savename = "attracont.mp4"`: 動画出力ファイルの名前。
  * `framerate = 4`: 動画出力のフレームレート。
  * `Δt, T`: アトラクタからサンプリングされた初期条件を進化させるために `trajectory` に伝播されます。
  * また、すべての [共通プロットキーワード](@ref common_plot_kwargs)。
  * `figure, axis, fracaxis, legend`: `Figure`、`Axis`、割合を含む「バーのような」軸、および凡例を追加する `axislegend` の作成にキーワード引数として伝播される名前付きタプル。
  * `add_legend = true`: 軸の凡例を表示するかどうか。
