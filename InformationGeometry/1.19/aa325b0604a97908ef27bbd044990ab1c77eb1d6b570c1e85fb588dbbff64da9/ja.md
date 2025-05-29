```
MultistartFit(DM::AbstractDataModel; maxval::Real=1e5, MultistartDomain::HyperCube=FullDomain(pdim(DM), maxval), kwargs...)
```

`N` 回のスタートと `timeout` 秒後のフィッティングのタイムアウトでマルチスタート最適化を実行します。`resampling=true` の場合、尤度が非有限の場合は新しい初期スタートが再描画され、`N` 個の適切な初期値が見つかるまで続けられます。`Robust=true` の場合、与えられたキーワード引数 `p` に従って p-ノルムに関して最適化を行います。`Full=false` の場合、最終的な MLE のみが返されますが、そうでない場合は `MultistartResults` オブジェクトが返され、さらに分析やプロットが可能です。キーワード `TransformSample` を使用して、サンプルに適用される関数を指定することができ、例えばパラメータのサブセットのみをサンプリングし、マルチスタートのために固定初期値のままにしておくべきコンポーネントを追加することができます。

!!! note
    その他のキーワード引数は、最適化手順 [`InformationGeometry.minimize`](@ref) に渡され、許容誤差、最適化手法、ドメイン制約などが含まれます。

