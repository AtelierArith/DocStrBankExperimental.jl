```
rand(r::ArbField; randtype::Symbol=:urandom)
```

与えられたArbフィールドのランダムな要素を返します。

`randtype`のデフォルトは`:urandom`で、$[0,1]$に含まれる`ArbFieldElem`を返します。

残りのメソッドは、コーナーケースを扱うために非一様に分布した値を返します。オプション`:randtest`は有限の数を返し、`:randtest_exact`は同じですが半径がゼロです。オプション`:randtest_precise`は、中央値の大きさの$2^{-\mathrm{prec}}$の周りに半径を持つ`ArbFieldElem`を返し、`:randtest_wide`は中央値に対して大きいかもしれない半径を返します。`:randtest_special`オプションは、値が`NaN`または`inf`である中央値と半径を返すことがあります。
