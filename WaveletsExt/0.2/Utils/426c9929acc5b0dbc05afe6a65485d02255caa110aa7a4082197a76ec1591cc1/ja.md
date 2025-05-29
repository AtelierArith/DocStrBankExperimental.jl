```
getchildindex(idx, child)
```

親インデックス `idx` の子インデックスを取得します。

# 引数

  * `idx::T where T<:Integer`: 親ノードのインデックス。
  * `child::Symbol`: 子のタイプ。二分木の場合、利用可能な子は `:left` と `:right` です。四分木の場合、利用可能な子は `:topleft`、`:topright`、`:bottomleft`、`:bottomright` です。

# 戻り値

  * `::T`: 子ノードのインデックス。

# 例

```repl
using WaveletsExt

getchildindex(3,:left) == 6
getchildindex(3,:right) == 7
getchildindex(3,:topleft) == 22
getchildindex(3,:topright) == 23
getchildindex(3,:bottomleft) == 24
getchildindex(3,:bottomright) == 25
```
