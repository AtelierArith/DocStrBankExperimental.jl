```
pix_get_dimensions(
    pix::Pix
)::Union{NamedTuple{(:w, :h, :d), Tuple{Int32, Int32, Int32}}, Nothing}
```

画像の寸法を取得します。

**引数:**

|   T | 名前  | デフォルト | 説明         |
| ---:|:--- |:----- |:---------- |
|   R | pix |       | 寸法を取得する画像。 |

**詳細:**

このメソッドは名前付きタプルを返します：

  * w - 画像の幅。
  * h - 画像の高さ。
  * d - カラーデプス。

参照：[`pix_get_depth`](@ref)
