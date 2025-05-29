```
Subsystem{T, Eltype, StateNT, ParamNT}
```

`Subsystem`構造体は`GraphSystem`の完全なサブコンポーネントを記述します。これは、サブシステムの連続的な動的状態を記述する`SubsystemStates`と、サブシステムのさまざまな非動的パラメータを記述する`GraphSystemParams`を格納します。型パラメータ`T`は、サブシステムの「タグ」であり、どのようなサブシステムであるかを示します。

`subsystem_differential`、`SubsystemStates`、`SubsystemParams`も参照してください。

たとえば、あるサブコンポーネントがビリヤードボールであるシステムを記述したい場合、
