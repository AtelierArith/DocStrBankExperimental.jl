```
transitionfrequency(I::Ion, transition::Tuple; B=0, ignore_manualshift=false)
```

`transition` は二つのサブレベルまたはレベルのタプルです。

`transition[1]` と `transition[2]` の間のエネルギーの差の絶対値を計算します。

サブレベル間の場合、磁場の値 `B` を設定することでゼーマンシフトを含めることができ、`ignore_manualshift=true` を設定することで手動シフトを省略することができます。
