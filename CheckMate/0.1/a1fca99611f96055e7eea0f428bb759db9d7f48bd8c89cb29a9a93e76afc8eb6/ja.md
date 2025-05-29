```
pass_rate(summary::CheckSummary)::Float64
```

すべてのチェックに合格した行の割合を計算します。

# 引数

  * `summary::CheckSummary`: 複数のチェックの結果を含むサマリーオブジェクト。

# 戻り値

すべてのチェックに合格した行の割合（0-100）を小数点以下1桁に四捨五入したもの。

# 例

```julia
rate = pass_rate(summary)  # 95%の行がすべてのチェックに合格した場合、95.0を返します
```
