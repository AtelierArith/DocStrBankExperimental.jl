```
@imagematrix drawing-instructions [width=256] [height=256]
```

描画を作成し、画像の行列を返します。

このマクロは、ベクターグラフィックスの指示によって生成された描画を表すピクセルの行列を返します。`image_as_matrix()`関数を使用します。

デフォルトの描画は256×256ポイントです。

`finish()`は必要ありません（マクロが呼び出します）、また`preview()`によってプレビューされることはありません。

```julia
julia> m = @imagematrix begin
               sethue("red")
               box(O, 20, 20, :fill)
           end 60 60;

julia> m[1220:1224]
5-element Array{ARGB32,1} with eltype ColorTypes.ARGB32:
 ARGB32(0.0N0f8,0.0N0f8,0.0N0f8,0.0N0f8)
 ARGB32(1.0N0f8,0.0N0f8,0.0N0f8,1.0N0f8)
 ARGB32(1.0N0f8,0.0N0f8,0.0N0f8,1.0N0f8)
 ARGB32(1.0N0f8,0.0N0f8,0.0N0f8,1.0N0f8)
 ARGB32(1.0N0f8,0.0N0f8,0.0N0f8,1.0N0f8)
```

もし、何らかの奇妙な理由で行列を別のLuxor描画として再描画したい場合は、次のようなコードを使用します：

```julia
m = @imagematrix begin
        sethue("red")
        box(O, 20, 20, :fill)
        sethue("blue")
        box(O, 10, 40, :fill)
    end 60 60

function convertmatrixtocolors(m)
    return convert.(Colors.RGBA, m)
end

function drawimagematrix(m)
    d = Drawing(500, 500, "/tmp/temp.png")
    origin()
    w, h = size(m)
    t = Tiler(500, 500, w, h)
    mi = convertmatrixtocolors(m)
    for (pos, n) in t
        c = mi[t.currentrow, t.currentcol]
        setcolor(c)
        box(pos, t.tilewidth -1, t.tileheight - 1, :fill)
    end
    finish()
    return d
end

drawimagematrix(m)
```

透明性

画像行列のセルのデフォルト値は透明な黒です。（Luxorのデフォルト色は不透明な黒です。）

```julia
julia> @imagematrix begin
       end 2 2
2×2 reinterpret(ColorTypes.ARGB32, ::Matrix{UInt32}):
 ARGB32(0.0,0.0,0.0,0.0)  ARGB32(0.0,0.0,0.0,0.0)
 ARGB32(0.0,0.0,0.0,0.0)  ARGB32(0.0,0.0,0.0,0.0)
```

背景を部分的または完全に透明な値に設定すると、予期しない結果が得られる場合があります：

```julia
julia> @imagematrix begin
           background(1, 0.5, 0.0, 0.5) # 半透明のオレンジ
       end 2 2
2×2 reinterpret(ColorTypes.ARGB32, ::Matrix{UInt32}):
 ARGB32(0.502,0.251,0.0,0.502)  ARGB32(0.502,0.251,0.0,0.502)
 ARGB32(0.502,0.251,0.0,0.502)  ARGB32(0.502,0.251,0.0,0.502)
```

ここでは、半透明のオレンジ色が透明な背景に部分的に適用されています。

```julia
julia> @imagematrix begin
           sethue(1., 0.5, 0.0)
           paint()
       end 2 2
2×2 reinterpret(ColorTypes.ARGB32, ::Matrix{UInt32}):
 ARGB32(1.0,0.502,0.0,1.0)  ARGB32(1.0,0.502,0.0,1.0)
 ARGB32(1.0,0.502,0.0,1.0)  ARGB32(1.0,0.502,0.0,1.0)
```

デフォルトのアルファ値1.0を取得します。
