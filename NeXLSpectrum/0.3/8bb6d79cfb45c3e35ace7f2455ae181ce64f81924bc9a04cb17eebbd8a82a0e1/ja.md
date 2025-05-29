```
Spectrum{T<:Real} <: AbstractVector{T}

Spectrum(energy::EnergyScale, data::Vector{<:Real}, props::Dict{Symbol,Any})
```

スペクトルデータ（エネルギースケール、カウント、メタデータ）を保持する構造体を構築します。

[`NeXLSpectrum.EnergyScale`](@ref) または [`NeXLSpectrum.LinearEnergyScale`](@ref) を参照してください。

例:

```
julia> spec = Spectrum(LinearEnergyScale(0.0,10.0),
                 collect(1:1024),
                 Dict{Symbol,Any}(:BeamEnergy=>10.0e3, :LiveTime=>30.0))
                                                                              ** 1024.0
                                                                       *********
                                                               *****************
                                                        ************************
                                                 *******************************
                                          **************************************
                                   *********************************************
                            ****************************************************
                     ***********************************************************
              ******************************************************************
       *************************************************************************
******************************************************************************** 10.0 keV
Spectrum[3062][10.0 keV, Unknown, 525000.0 counts]
```

スペクトルは通常、ディスクから次のように読み込まれます:

```
s1 = loadspectrum(joinpath(path,"ADM-6005a_1.msa")) # 自動的にファイルタイプを検出します（ISO/EMSA、Bruker、ASPEX、???ファイルをサポート）
  *                                                                                                  128860.0
  *
  *
  *
  *
  *
  *     *
  *     *
  *     *
  * ** **
  * ** *****        **  **
**************************************************************************************************** 20.0 keV
Spectrum{Float64}[ADM-6005a_1, -484.20818 + 5.01716⋅ch eV, 4096 ch, 20.0 keV, Unknown, 6.81e6 counts]
```

`Spectrum` はさまざまなメカニズムを使用してインデックスを実装しています。 `spec` が `Spectrum` の場合、

```
spec[123] # チャンネル123のカウント数を返します
spec[123:222] # チャンネル123:222のカウントのベクトルを返します
spec[134.] # エネルギー134.0 eVのチャンネルのカウント数を返します
spec[134.0:270.0] # エネルギー134.0 eVから270.0 eVの間のチャンネルのカウントのベクトルを返します
spec[n"Ca L3-M5"] # Ca L3-M5特性X線エネルギーのチャンネルのカウント
spec[:Comment] # :Commentという名前のメタデータ項目を返します
```

基本的なスペクトル数学は、演算子 *, /, ÷, +, および - を使用してサポートされています。 `s1`、`s2`、および `s3` が `Spectrum` オブジェクトである場合：

```
2*s1 # 各チャンネルに2倍のカウントを含むスペクトル
2.0*s1 # 各チャンネルに2倍のカウントを含むスペクトル
s1/2.0 # 各チャンネルに半分のカウントを含むスペクトル
s1÷2 # 各チャンネルに半分のカウントを含むスペクトル（Spectrum{<:Integer} のみで動作）
s1 + s2 # s1とs2のカウントのチャンネルごとの合計を含むスペクトル
s1 - s2 # チャンネルごとの差
```

スペクトルメタデータは `Symbol` によって識別されます。これらの `Symbol` は NeXLSpectrum 内で使用されます。他のデータ項目を `Spectrum` に関連付けるために他のものを作成できます。

```
:BeamEnergy    # eV単位
:Elevation     # ラジアン単位
:TakeOffAngle  # ラジアン単位（検出器位置）
:Azimuthal     # ラジアン単位（検出器位置）
:WorkingDistance # cm単位（mmではありません!!!!）
:LiveTime      # 秒単位
:RealTime      # 秒単位
:DeadFraction  # 割合
:ProbeCurrent  # ナノアンペア単位
:Name          # `String`
:Owner         # `String`
:Sample        # サンプルの説明
:StagePosition # :X, :Y, :Z, :R, :Tのエントリを持つDict{Symbol,Real}（cmおよび度単位）
:Comment       # `String`
:Composition   # `Material`（既知の組成、測定されていない）
:Elements      # `[ n"Fe", n"Ca", n"Si" ]` のような材料内の元素のコレクション
:Detector      # BasicEDSや他のEDSDetectorのような検出器
:Filename      # ソースファイル名
:Coating       # `Film` または `Film[]`（例：10 nmのC|Auなど）
:AcquisitionTime # 取得日時（`DateTime` 構造体）
:Signature     # "粒子署名"を持つDict{Element,Real}
:SolidAngle    # 検出器の固体角はステラジアン（面積/距離²）
```

スペクトル画像項目:

```
:ImageRotation # :X軸から:Y軸への主スキャン方向の回転（ラジアン単位）
```

あまり一般的でない項目:

```
:ImageMag	   # 最初の画像の拡大率（3.5インチの画像を仮定）
:ImageZoom     # 2つの画像のTIFFでの2番目の画像の追加ズーム
:Operator      # ASPEX TIFFファイルのアナリスト
:Image1, :Image2 ... # スペクトルに関連付けられた画像
:BrukerThroughtput # Bruker検出器の名目スループット設定
:DetectorSerialNumber # EDS検出器のシリアル番号
:DetectorModel # ベンダーモデル名
:DetectorThickness # 検出器のアクティブエリアの厚さ
:DeadLayerThickness # 検出器の入口表面のSiデッドレイヤーの厚さ
:Window        # ウィンドウの構造詳細
:DetectorSolidAngle # X線検出器のコレクション固体角
:ChamberPressure # サンプルチャンバー内の真空圧
:ChamberAtmosphere # チャンバー内の残留ガスの名目組成
```

XRF関連項目:

```
:BeamEnergy  # X線管内の加速電圧（eV）
:XRFTubeAnode    # X線管が構成されている元素
:ProbeCurrent  # X線管内の電子電流
:XRFTubeIncidentAngle # 管内の電子ビームの入射角
:XRFTubeTakeOffAngle # 管からの取り出し角
:XRFExcitationAngle # サンプルに対するX線ビームの入射角
:XRFDetectionAngle # サンプルに対する検出器の角度
:XRFExcitationPathLength # X線源からサンプルまでの距離
:XRFDetectionPathLength # サンプルからX線検出器までの距離
:XRFSampleTilt    # サンプルの追加傾き
:XRFTubeWindow   # 管ウィンドウの構造
```

すべてのスペクトルがすべてのプロパティを定義するわけではありません。アルゴリズムは `NeXLCore.minproperties(ty::Type)` メソッドを定義して、`ty::Type` のアルゴリズムに必要なプロパティを指定できます。次に、`hasminrequired` および `requiredbutmissing` メソッドが、`Spectrum` または `Dict{Symbol,Any}` がアルゴリズムに適しているかどうかを判断します。 ```
