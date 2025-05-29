```
Legend
```

これは `MultiCoefplot.legend` に入ります。これは凡例のスタイルを決定します。凡例の内容は `Coefplot` のタイトルによって定義されます。

# コンストラクタ

```julia
Legend(;anchor=missing, at=missing, font=missing, size=missing)
```

# キーワード引数

  * `anchor::Union{Symbol, String, Missing}` は、整列に使用される凡例ボックスのアンカーを指定します。一般的なものは `"north west"` です。
  * `at::Any` は、アンカーが従うべき軸フレーム内の位置を指定します。一般的なものは `(1, 0)` で、これはアンカーが軸フレームの南東隅に固定されることを意味します。
  * `font::Union{Symbol, String, Missing}` は、凡例が印刷されるフォントです。
  * `size::Union{Real, Missing}` は、フォントサイズです。
