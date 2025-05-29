```
symboltoint(pstr::Union{Vector{Symbol}, Symbol})
```

シンボルまたはシンボルのベクター `pstr` を整数パウリ文字列にマッピングします。

# 例

```
symboltoint([:X, :I])

# 出力

0x01
```
