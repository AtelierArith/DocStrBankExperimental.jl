```
fixed(args...)
```

パラメータを特定の値に固定します。アンサンブルモデルの場合、複数の値（各サブモデル/グループごとに1つ）が必要です。

# 例

```julia
graph = @StenoGraph begin
    x → fixed(1)*y
end
```
