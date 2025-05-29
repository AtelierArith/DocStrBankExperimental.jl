```
fracdiff(x,d::Int)
```

時系列 `x` の一次または零差分を計算します。複数のディスパッチを使用して、`d=1` または `d=0` の場合には同じ入力を返すか、Julia標準ライブラリの `diff` 関数を呼び出します。

# 引数

  * `x::Vector`: 時系列
  * `d::Int64`: 差分パラメータ

# 出力

  * `dx::Vector`: `x` の一次または零差分

# 例

```julia-repl
julia> fracdiff(randn(100,1),1)
```
