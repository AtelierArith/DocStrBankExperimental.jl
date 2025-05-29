```
DeviceRAModel{D <: PSY.Device, B <: AbstractRAFormulation}
```

# 引数

  * D <: PSY.Device: デバイスタイプ

      * `formulation::SiennaPRASInterface.AbstractRAFormulation`: 設定を含む定式化

DeviceRAModelは、PowerSimulationsのDeviceModelのように、特定の定式化にコンポーネントのタイプを割り当てます。Siennaとは異なり、設定情報を定式化自体に入れます。
