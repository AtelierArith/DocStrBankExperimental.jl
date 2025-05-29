```
stack(t, by = pkeynames(t); select = Not(by), variable = :variable, value = :value)`
```

テーブルをワイド形式からロング形式に変形します。`by`の列はインデックス列として保持されます。`select`の列はスタックされます。ID列に加えて、列識別子とスタックされた列を含む`variable`および`value`という2つの追加列が追加されます。詳細は[`unstack`](@ref)を参照してください。

# 例

```
t = table(1:4, names = [:x], pkey=:x)
t = pushcol(t, :xsquare, :x => x -> x^2)
t = pushcol(t, :xcube  , :x => x -> x^3)

stack(t)
```
