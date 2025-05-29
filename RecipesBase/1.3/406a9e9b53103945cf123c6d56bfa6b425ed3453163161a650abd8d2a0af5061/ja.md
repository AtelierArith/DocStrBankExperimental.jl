```
@shorthands(funcname::Symbol)
```

ショートハンドプロットメソッド定義（`$funcname` と `$funcname!`）を定義してエクスポートします。マクロにシリーズタイプ（シンボルとして）を渡します。

## 例

```julia
# シリーズタイプを定義する
@recipe function f(::Type{Val{:myseriestype}}, x, y)
    # ここに実装を記述
end
# ドキュメント文字列は転送されます
"""
    myseriestype(x, y)
私のシリーズタイプをプロットします！
"""
@shorthands myseriestype
```
