```
gettreelength(n[, m])
```

バイナリ/クワッドツリー `BitVector` の長さを計算します。

# 引数

  * `n::T where T<:Integer`: 1次元の配列サイズ/1D信号の信号長。
  * `m::T where T<:Integer`: 2次元の配列サイズ。

# 戻り値

  * `::T`: バイナリ/クワッドツリーの長さ。

# 例

```repl
using WaveletsExt

Utils.gettreelength(8)          # 7
Utils.gettreelength(8,8)        # 21
```
