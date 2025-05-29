```
raster_pullback!(
    ds_dout, args...;
    [points, rotation, translation, background, out_weight, point_weight]
)
```

[`raster`](@ref) / [`raster!`](@ref) のプルバック。

入力として `ds_dout` を受け取り、これは関数 `out = raster(grid_size, args...)` (または `out = raster!(out, args...)`) の出力 `out` に対するある量 (`s` は「スカラー」を意味する) の感度であり、`raster`/`raster!` に渡されたのと全く同じ引数 `args` を受け取り、関数 `raster`/`raster!` の入力 `args` に対する `s` の感度を返します。

オプションとして、各入力感度のための事前に割り当てられた出力配列を、元の引数の名前をキーとして、nd-arrayを値としてキーワード引数として指定できます。ここで、n次元目はバッチ次元です。例えば、`raster` の `translation` 引数に対する `s` の感度のために事前に割り当てられた配列を提供するには、次のようにします: `sensitivities = raster_pullback!(ds_dout, args...; translation = [zeros(2) for _ in 1:8])` これは2次元のポイントとバッチサイズ8の場合です。また、[単一のポイントクラウドをポーズのバッチにラスタリングする](@ref)も参照してください。
