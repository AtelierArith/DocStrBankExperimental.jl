`BoundingBox()` 引数なしで呼び出すと、現在の描画を含む BoundingBox が返されます。

デフォルトの `BoundingBox(;centered=true)` は、現在の描画と同じサイズと位置の BoundingBox を返し、原点 (0, 0) が中心にあると仮定します。

`centered` オプションが `false` の場合、関数は原点が描画の左上にあると仮定します。したがって、この関数は現在の行列が変更されている場合（`translate()`、`scale()`、`rotate()` などによって）には正しく機能しません。

BoundingBox 型のインスタンスは、`corner1` と `corner2` の2つのポイントを保持します。

```julia
BoundingBox(;centered = true)   # 描画のバウンディングボックス
```

```julia
BoundingBox(s::AbstractString)  # 原点でのテキスト文字列のバウンディングボックス
```

```julia
BoundingBox(pt::Array)          # 多角形のバウンディングボックス
```

```julia
BoundingBox(circle(O, 100))     # circle() によって追加されたパスのバウンディングボックス
```

```julia
BoundingBox(path::Path)         # Path のバウンディングボックス
```

`BoundingBox()` を、現在のパスにグラフィックシェイプを追加する関数（例：`box()`、`circle()`、`star()`、`ngon()`）と一緒に使用できます。ただし、例えば `BoundingBox(box(O, 100, 100))` は、バウンディングボックスを返すだけでなく、現在のパスにもシェイプを追加することに注意してください。
