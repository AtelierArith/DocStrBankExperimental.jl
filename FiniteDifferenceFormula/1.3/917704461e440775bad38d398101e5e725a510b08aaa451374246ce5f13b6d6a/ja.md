`decimalplaces`() または `decimalplaces`(n)

引数が `decimalplaces` に渡されない場合、計算された数式のJulia関数を生成するための現在の小数点以下の桁数を表示します。それ以外の場合は、小数点以下の桁数を n に設定します。

# 例

```
import FiniteDifferenceFormula as fd
fd.compute(2,-3:3)
fd.formula()  # デフォルトでは、16桁の小数点以下を使用してJulia関数を生成
fd.decimalplaces(4)
fd.formula()  # 現在は、4桁の小数点以下を使用してJulia関数を生成
```
