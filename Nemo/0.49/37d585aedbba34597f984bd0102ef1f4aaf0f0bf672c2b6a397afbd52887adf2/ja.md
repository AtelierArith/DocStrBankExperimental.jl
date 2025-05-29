```
rand(r::RealField; randtype::Symbol=:urandom)
```

与えられたArbフィールドのランダム要素を返します。

`randtype`のデフォルトは`:urandom`で、$[0,1]$に含まれる`ArbFieldElem`を返します。

残りのメソッドは、コーナーケースを扱うために非一様に分布した値を返します。オプション`:randtest`は有限の数を返し、`:randtest_exact`は同じですが半径がゼロです。オプション`:randtest_precise`は、$2^{-\mathrm{prec}}$の半径を持つ`ArbFieldElem`を返し、`:randtest_wide`はその中点に対して大きいかもしれない半径を返します。`:randtest_special`オプションは、中点と半径の値が`NaN`または`inf`である可能性があります。
