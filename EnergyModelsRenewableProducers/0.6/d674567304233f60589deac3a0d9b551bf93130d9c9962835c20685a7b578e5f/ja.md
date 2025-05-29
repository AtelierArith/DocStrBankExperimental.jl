`EnergyModelsRenewableProducers.jl`のメインモジュール。

このモジュールは、以下のタイプ（ノード）を制約付きで実装しています：

  * `NonDisRes`は`Source`のサブタイプで、風力、太陽光などの非調整可能な再生可能エネルギー生産者を表します。
  * `PumpedHydroStor`は`Storage`のサブタイプで、調整された揚水発電所を表します。
  * `HydroStor`は`Storage`のサブタイプで、ポンプのない標準的な水力発電所である調整された水力貯蔵を表します。
  * `HydroReservoir`は`Storage`のサブタイプで、連鎖水力発電システムのための水力貯蔵を表します。
  * `HydroGenerator`は`Network`のサブタイプで、連鎖水力発電システムのための水力発電機を表します。
  * `HydroPump`は`Network`のサブタイプで、連鎖水力発電システムのための水力ポンプを表します。
  * `HydroGate`は`Network`のサブタイプで、連鎖水力発電システムのためのゲートを表します。
