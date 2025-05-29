```
rmlines(x)
```

ブロックまたは式の配列から行ノードを削除します。

`quote end` と `rmlines(quote end)` を比較してください。

### 例

ネストされたブロックで作業するには:

```julia
prewalk(rmlines, ex)
```

関連情報: [`@q`](@ref)
