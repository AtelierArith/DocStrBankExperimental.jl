```
label(args...)
```

ラベルパラメータ。アンサンブルモデルの場合、複数の値（各サブモデル/グループごとに1つ）が必要です。

# 例

```julia
graph = @StenoGraph begin
    x → label(:a)*y
end
```
