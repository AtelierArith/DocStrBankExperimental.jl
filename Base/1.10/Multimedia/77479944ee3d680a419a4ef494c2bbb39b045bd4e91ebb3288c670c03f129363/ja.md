```
pushdisplay(d::AbstractDisplay)
```

グローバルディスプレイバックエンドスタックの上に新しいディスプレイ `d` をプッシュします。 `display(x)` または `display(mime, x)` を呼び出すと、スタック内の最上位の互換性のあるバックエンド（すなわち、[`MethodError`](@ref) をスローしない最上位のバックエンド）で `x` が表示されます。
