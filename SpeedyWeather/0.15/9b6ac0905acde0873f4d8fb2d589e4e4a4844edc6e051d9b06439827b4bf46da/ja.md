水平超拡散の渦、発散、温度、湿度; スペクトル空間で暗黙的にラプラシアンの`power`（デフォルト = 4）を使用し、強度は`time_scale`（デフォルト = 1時間）によって制御されます。渦度と発散については、デフォルトで`time_scale`（=拡散の強度の逆数）が`resolution_scaling`を通じて解像度の増加に伴い減少し、パワーは`tapering_σ`シグマレベルの上で垂直方向に線形に減少して`power_stratosphere`（デフォルト2）になります。

BarotropicModelおよびShallowWaterModelにはテーパリングやスケーリングは適用されません。フィールドとオプションは次のとおりです。

  * `trunc::Int64`: スペクトル解像度
  * `nlayers::Int64`: 垂直レベルの数
  * `power::Any`: [OPTION] ラプラシアンのパワー
  * `time_scale::Dates.Second`: [OPTION] 拡散の時間スケール
  * `time_scale_div::Dates.Second`: [OPTION] 温度と湿度の拡散時間スケール
  * `resolution_scaling::Any`: [OPTION] 解像度による強い拡散？ 0: truncで一定、1: truncで（逆）線形、など
  * `power_stratosphere::Any`: [OPTION] トロポポーズ/成層圏のための異なるパワー
  * `tapering_σ::Any`: [OPTION] このσの上でpower_stratosphereに向かって線形にスケール
  * `expl::Any`
  * `impl::Any`
  * `expl_div::Any`
  * `impl_div::Any`
