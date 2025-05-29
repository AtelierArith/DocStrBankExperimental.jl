```
unstack(t, by = pkeynames(t); variable = :variable, value = :value)
```

テーブルをロング形式からワイド形式に変形します。`by`の列はインデックス列として保持されます。キーワード引数`variable`と`value`は、どの列が列識別子を含み、どの列が対応する値を含むかを示します。詳細は[`stack`](@ref)を参照してください。

# 例

```
t = table(1:4, [1, 4, 9, 16], [1, 8, 27, 64], names = [:x, :xsquare, :xcube], pkey = :x);

long = stack(t)

unstack(long)
```
