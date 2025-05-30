```
PISCES(; grid::AbstractGrid{FT},
         phytoplankton = MixedMondoNanoAndDiatoms(),
         zooplankton = MicroAndMesoZooplankton(),
         dissolved_organic_matter = DissolvedOrganicCarbon(),
         particulate_organic_matter = TwoCompartementCarbonIronParticles(),
         
         nitrogen = NitrateAmmonia(),
         iron = SimpleIron(),
         silicate = Silicate(),
         oxygen = Oxygen(),
         phosphate = Phosphate(),
         
         inorganic_carbon = InorganicCarbon(),

         # Aumount 2005から2015ではなく、逆に動作しないため
         first_anoxia_thresehold = 6.0,
         second_anoxia_thresehold = 1.0,

         nitrogen_redfield_ratio = 16/122,
         phosphate_redfield_ratio = 1/122,
         
         mixed_layer_shear = 1.0,
         background_shear = 0.01, 
         
         latitude = PrescribedLatitude(45),
         day_length = day_length_function,
         
         mixed_layer_depth = Field{Center, Center, Nothing}(grid),
         euphotic_depth = Field{Center, Center, Nothing}(grid),

         silicate_climatology = ConstantField(7.5),

         mean_mixed_layer_vertical_diffusivity = Field{Center, Center, Nothing}(grid),
         mean_mixed_layer_light = Field{Center, Center, Nothing}(grid),

         carbon_chemistry = CarbonChemistry(),
         calcite_saturation = CenterField(grid),

         surface_photosynthetically_active_radiation = default_surface_PAR,

         light_attenuation =
           MultiBandPhotosyntheticallyActiveRadiation(; grid, 
                                                        surface_PAR = surface_photosynthetically_active_radiation),

         sinking_speeds = (POC = 2/day, 
                           # これを事前に計算する方が効率的かもしれない
                           GOC = Field(KernelFunctionOperation{Center, Center, Face}(DepthDependantSinkingSpeed(), 
                                                                                     grid, 
                                                                                     mixed_layer_depth, 
                                                                                     euphotic_depth))),
         open_bottom = true,

         scale_negatives = false,
         invalid_fill_value = NaN,
         
         sediment = nothing,
         particles = nothing,
         modifiers = nothing)
```

PISCES生物地球化学モデルのインスタンスを構築します。

# キーワード引数

  * `grid`: (必須) モデルを構築するためのジオメトリ
  * `phytoplankton`: 植物プランクトンの進化パラメータ化、デフォルトはnanophytoおよびdiatomサイズクラスで`MixedMondo`成長
  * `zooplankton`: 動物プランクトンの進化パラメータ化、デフォルトは2クラス`Z`および`M`
  * `dissolved_organic_matter`: 溶存有機物（`DOC`）の進化のためのパラメータ化
  * `particulate_organic_matter`: 粒子状有機物（`POC`, `GOC`, `SFe`, `BFe`, `PSi`, `CaCO₃`）の進化のためのパラメータ化
  * `nitrogen`: 窒素コンパートメント（`NH₄`および`NO₃`）のためのパラメータ化
  * `iron`: 鉄（`Fe`）のためのパラメータ化、現在のところAumount 2015の「複雑な化学」は実装されていません
  * `silicate`: ケイ酸塩（`Si`）のためのパラメータ化
  * `oxygen`: 酸素（`O₂`）のためのパラメータ化
  * `phosphate`: リン酸塩（`PO₄`）のためのパラメータ化
  * `inorganic_carbon`: 無機炭素系の進化のためのパラメータ化（`DIC`および`Alk`alinity）
  * `first_anoxia_thresehold`および`second_anoxia_thresehold`: 無酸素状態のパラメータ化における閾値
  * `nitrogen_redfield_ratio`および`phosphate_redfield_ratio`: 仮定される元素比N/CおよびP/C
  * `mixed_layer_shear`および`background_shear`: 混合層および背景せん断速度、TODO: これを計算フィールドに移動
  * `latitude`: モデルの緯度、`RectilinearGrid`の場合は`PrescribedLatitude`、独自の緯度を提供するグリッドの場合は`ModelLatitude`であるべき
  * `day_length`: 年間の時間と緯度に基づく日長のためのパラメータ化、日長の影響を無視したい場合は(φ, t) -> 1dayに変更するか、異なる惑星をモデル化している場合は他の何かに変更することをお勧めします
  * `mixed_layer_depth`: 混合層の深さを含む`AbstractField`（状態更新中に計算される）
  * `euphotic`: 光が表面値の1/1000に減少する深さを含む`AbstractField`（状態更新中に計算される）
  * `silicate_climatology`: ダイオウイカのケイ酸塩半飽和定数に影響を与えるケイ酸塩気候学を含む`AbstractField`
  * `mean_mixed_layer_vertical_diffusivity`: 平均混合層垂直拡散率を含む`AbstractField`（状態更新中に計算される）
  * `mean_mixed_layer_light`: 平均混合層光を含む`AbstractField`（状態更新中に計算される）
  * `carbon_chemistry`: カルサイト飽和を計算するために使用される`CarbonChemistry`モデル
  * `calcite_saturation`: カルサイト飽和を含む`AbstractField`（状態更新中に計算される）
  * `surface_photosynthetically_active_radiation`: 表面での光合成可能な放射線の関数
  * `light_attenuation_model`: 利用可能な光の減衰を統合する光減衰モデル
  * `sinking_speed`: 定数の沈降速度の名前付きタプル、または沈降する任意のトレーサーのフィールド（すなわち`ZFaceField(...)`）（沈降速度は正であるべきですが、フィールドは通常の下向きが負である必要があります）
  * `open_bottom`: トレーサーがドメインを離れないように、沈降速度を底で滑らかにゼロにするべきか
  * `scale_negatives`: 負のトレーサーをスケールするか？
  * `particles`: `BiogeochemicalParticles`のスロット
  * `modifiers`: 傾向が計算されたときや状態が更新されたときに生物地球化学を修正するコンポーネントのスロット

すべてのパラメータ化は、PISCESの運用バージョンにできるだけ近いデフォルトです。

# 注意事項

現在、`MixedMondoPhytoplankton`のみが実装されており、必要に応じてクラスを単一の`phytoplankton`に一般化する作業が必要です（`OceanBioME.Models.PISCESModel`のドキュメント文字列を参照）。同様に、より一般的な`particulate_organic_matter`が必要な場合は、引数のために任意のトレーサーを指定する方法が必要です。
