```
moist_air(humidity [, pressure=c_p_ref, temp=c_T_ref])
```

相対湿度に対する湿った空気の成分リストを返し、すべての成分の対応する存在量を示します。圧力（atm単位）と温度（K単位）を提供する必要があり、そうでない場合はHITRANのデフォルト値が使用されます。

!!! info "有効範囲"
    飽和水蒸気圧の基礎となるモデルは、水と氷のために別々のモデルを使用していることに注意してください。200 Kから400 Kの範囲および0.6 atmから1.1 atmの間で合理的な値を提供するはずです。

