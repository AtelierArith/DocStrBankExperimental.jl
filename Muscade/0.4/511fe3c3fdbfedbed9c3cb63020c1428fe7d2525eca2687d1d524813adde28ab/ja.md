```
draw(state[,els];kwargs...)
```

`state` は単一の `State` です。`els` は描画する要素を指定し、次のいずれかになります。

  * `EleID` のベクトル（[`addelement!`](@ref) から取得）、すべて同じ具体的な要素タイプに対応
  * 具体的な要素タイプ（[`eletyp`](@ref) を参照）。
  * 省略された場合：モデルのすべての要素が描画されます。

`kwargs...` は、各要素の `draw` メソッドに渡される追加のキーワード引数で、色を指定するなどに使用されます。要素のドキュメントを参照してください。

関連情報: [`getdof`](@ref), [`@request`](@ref), [`@espy`](@ref), [`addelement!`](@ref), [`solve`](@ref)
