`formulas`(orders = 1:3, min*num*of*points = 2, max*num*of*points = 5)

デフォルトでは、この関数は1次、2次、3次の導関数に対するすべての前進、後退、中央の有限差分公式を、2から5ポイントを使用して印刷します。

# 例

```julia-repl
# 次の例は、指定された導関数に対するすべての前進、後退、中央の有限差分
# 公式を、4から11ポイントを使用して示しています。
julia> import FiniteDifferenceFormula as fd
julia> fd.formulas(2:5, 4, 11)       # 2次、3次、..、5次の導関数
juliq> fd.formulas([2, 4, 7], 4, 11) # 2次、4次、7次の導関数
julia> fd.formulas(3, 4, 11)         # 3次の導関数
```
