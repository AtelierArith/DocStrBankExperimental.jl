```
IndicatorLöhner (equivalent to IndicatorLoehner)

IndicatorLöhner(equations::AbstractEquations, basis;
                f_wave=0.2, variable)
IndicatorLöhner(semi::AbstractSemidiscretization;
                f_wave=0.2, variable)
```

AMRインジケーターは、Löhner（1987）によるFEMインジケーターから適応され、FLASHコードで標準AMRインジケーターとしても使用されます。このインジケーターは、指定された変数の加重二次導関数をローカルに推定します。

AMR用に構築する場合は、`semi`を渡します。このインジケーターを衝撃捕捉に使用する場合は、`equations`と`basis`を渡します。

## 参考文献

  * Löhner (1987) "An adaptive finite element scheme for transient problems in CFD" [doi: 10.1016/0045-7825(87)90098-3](https://doi.org/10.1016/0045-7825(87)90098-3)
  * [https://flash.rochester.edu/site/flashcode/user*support/flash4*ug_4p62/node59.html#SECTION05163100000000000000](https://flash.rochester.edu/site/flashcode/user_support/flash4_ug_4p62/node59.html#SECTION05163100000000000000)
