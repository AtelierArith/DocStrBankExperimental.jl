```
Figure(; [figure_padding,] kwargs...)
```

`Block`のような[`Axis`](@ref)、[`Colorbar`](@ref)、[`Legend`](@ref)を内部に配置できる`Figure`を構築します。図の外側のパディング（コンテンツとエッジの距離）は、`figure_padding`キーワードを介して1つの数値または左、右、下、上のパディングの4つの数値のタプルを渡すことで設定できます。

`size`や`backgroundcolor`などの他のキーワード引数は、図が所有する[`Scene`](@ref)に転送され、すべての他の視覚オブジェクトのコンテナとして機能します。
