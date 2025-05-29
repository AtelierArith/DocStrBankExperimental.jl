```
gas_unit_converter(
    value_in::Unitful.Quantity,
    units_in::String,
    units_out::String;
    species::String="H",
    temperature=293.15 * Unitful.K,
)
```

異なる単位間でガスフローを変換します。圧力 * 体積タイプのフロー/量とカウント/電流タイプの単位間で変換するために理想気体の法則を使用します。これはUnitfulバージョンです。

出力は単位を持ちますが、単位は自動的に簡略化されません。次のような操作を行うことができます。

  * `(output |> Unitful.upreferred).val`
  * `Unitful.uconvert(Unitful.whatever, output).val`

単位の簡略化や変換を処理するために。

この関数はtorr L s$^{-1}$とPa m$^3$ s$^{-1}$が異なるものであるかのように振る舞いますが、Unitfulを使用すれば、最終的に単位を簡略化または変換する限り、同じように動作します。つまり、他の圧力*体積タイプのガス単位を使用し、それらをtorr L s$^{-1}$と呼ぶことができ、スクリプトは出力において混乱した単位を持つまでそれらを処理します。
