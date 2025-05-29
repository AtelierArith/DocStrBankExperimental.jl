```
findall_nan_chunks(x)
```

`x`の各`NaN`チャンクの`(start, stop)`インデックスを見つけ、`NaN`範囲のインデックスタプルのベクトルを返します。

関連情報: [`findall_nan_chunks!`](@ref)

## 例

```julia
x = [NaN, NaN, 2.3, NaN, 5.6, NaN, NaN, NaN]
findall_nan_chunks(x)
```
