```
anim_initialize!(canvas, renderer, domain, state;
                 callback=nothing, overlay=nothing, kwargs...)
```

`canvas`上でレンダリングされるアニメーションを初期化します。初期化ステップとして[`anim_plan`](@ref)および[`anim_trajectory`](@ref)によって呼び出されます。

デフォルトでは、これは単に初期`state`を`canvas`上にレンダリングします。この関数は、キャプションや他のオーバーレイを追加するために、異なる[`Renderer`](@ref)タイプに対してオーバーロードすることができます。
