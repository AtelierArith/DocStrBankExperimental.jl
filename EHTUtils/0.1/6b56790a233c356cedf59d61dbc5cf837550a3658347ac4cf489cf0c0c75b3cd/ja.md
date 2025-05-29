```
unitconv(unit1, unit2)
```

unit1からunit2への変換係数を導出します。unit1の値は、この変換係数を掛けることでunit2の値に変換できます。

# 例

```julia-repl
julia> # 1KをmKに変換
julia> val2 = 1 * unitconv(u"K", u"mK") # 値2は1000になります
```
