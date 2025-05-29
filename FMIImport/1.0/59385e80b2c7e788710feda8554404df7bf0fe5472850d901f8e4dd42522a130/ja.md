```
fmi3UpdateDiscreteStates(c::FMU3Instance)
```

この関数は、現在の超密な時間瞬間で収束した解を示すために呼び出されます。fmi3UpdateDiscreteStatesは、超密な時間瞬間ごとに少なくとも1回は呼び出す必要があります。結果が返されます。インプレースバリアントには`fmi3UpdateDiscreteStates!`を使用してください。

# 引数

  * `c::FMU3Instance`: FMU 3.0標準のインスタンス化されたFMUのインスタンスを表す可変構造体。

# 戻り値

  * `discreteStatesNeedUpdate`
  * `terminateSimulation`
  * `nominalsOfContinuousStatesChanged`
  * `valuesOfContinuousStatesChanged`
  * `nextEventTimeDefined`
  * `nextEventTime`

# 出典

  * FMISpec3.0 リンク: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec3.0: 2.2.3 プラットフォーム依存の定義
  * FMISpec3.0: 2.3.5. 状態: イベントモード

```
