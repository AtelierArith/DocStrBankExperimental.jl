```
render(
    renderables::AbstractVector;
    camera::Union{Nothing, Camera} = nothing,
    canvas_width::Int64 = (camera === nothing ? DEFAULT_CANVAS_WIDTH : canvas_width(camera)),
    canvas_height::Int64 = (camera === nothing ? DEFAULT_CANVAS_HEIGHT : canvas_height(camera)),
    surface::CairoSurface = CairoSVGSurface(IOBuffer(), canvas_width, canvas_height)
)
```

すべての `renderables` を `canvas_width` x `canvas_height` の `surface` に描画します。すべての renderable は、レンダリング指示をレンダーモデルに追加する `add_renderable!` 関数を実装する必要があります。

提供された `camera` は、`render` を呼び出す前に `update_camera!()` 関数を使用して更新する必要があります。カメラが提供されていない場合、レンダリング関数はすべてのレンダラブルオブジェクトをキャンバスにフィットさせることをデフォルトとします。
