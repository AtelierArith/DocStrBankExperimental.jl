```
plume(::Scenario, BritterMcQuaidPlume[, equationset::EquationSet])
```

与えられたシナリオに対するBritter-McQuaid連続地表放出モデルの解を返します。

`equationset`は10mでの風速を計算するために使用され、他のすべての相関はBritter-McQuaidモデルに従います。特に指定がない限り、デフォルトのべき法則風プロファイルが使用されます。

# 参考文献

  * Britter, Rex E. and J. McQuaid. 1988. *Workbook on the Dispersion of Dense Gases. HSE Contract Research Report No. 17/1988*
  * AIChE/CCPS. 1999. *Guidelines for Consequence Analysis of Chemical Releases*. New York: American Institute of Chemical Engineers
