```
imview(img::AbstractArray{<:Complex}; ...)
```

複素値を持つ画像に適用すると、`imview`を使用してピクセルの大きさを表示し、サイクルカラー マップを使用して下に位相角をパネルとして表示します。よりカスタマイズするには、次のように自分でビューを作成できます。

```julia
vcat(
    imview(abs.(img)),
    imview(angle.(img)),
)
```
