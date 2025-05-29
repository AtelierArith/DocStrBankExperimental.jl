典型的MRパルスのための構造体: `Pulse <: AbstractPulse`。

# フィールド:

*可変*:

  * `rf::TypeND(RF0D, [1,2])` (nT,) または (nT, nCoils)。
  * `gr::TypeND(GR0D, [2])` (nT, 3)、ここで3はx-y-zチャネルを考慮しています。
  * `dt::T0D` (1,)、シミュレーションの時間ステップサイズ、すなわち、ドウェルタイム。
  * `des::String`、構築されるパルスの説明。

# 使用例:

```
Pulse(rf, gr; dt=(4e-6)u"s", des="generic pulse")
```

参照: [`AbstractPulse`](@ref)。
