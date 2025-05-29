```
Csf = SysFilter(sys_discrete::StateSpace)
Csf = SysFilter(sys_continuous::StateSpace, sampletime)
Csf = SysFilter(sys::StateSpace, state::AbstractVector)
```

LTIシステムを通じて信号をフィルタリングするために使用されるオブジェクトを返します。LTIシステムを使用して制御ループやシミュレーターを実装するために使用できるSysFilterオブジェクトを作成します。すなわち、`U(z) = C(z)E(z)`。フィルターを通じて信号`u`をフィルタリングするには、`y = Csf(u)`のように呼び出します。`y = Cx+Du, x'=Ax+Bu`においてフィルタリングされた出力`y`を計算します。
