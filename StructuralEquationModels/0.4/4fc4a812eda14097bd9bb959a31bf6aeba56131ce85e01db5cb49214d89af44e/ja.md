```
start(args...)
```

パラメータの初期値を定義します。アンサンブルモデルの場合、複数の値（各サブモデル/グループごとに1つ）が必要です。

# 例

```julia
graph = @StenoGraph begin
    x → start(1)*y
end
```
