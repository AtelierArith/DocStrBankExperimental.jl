```
NeXLUncertainties.asa(
    ::Type{DataFrame}, 
    ffr::FilterFitResult; 
    charOnly::Bool=true, 
    material=nothing,
    mc = XPP, fc=ReedFluorescence,
    columns = ( :counts, ) # Selected from ( :roi, :peakback, :counts, :dose )
)::DataFrame
```

'FilterFitResult'内の各領域の詳細を'DataFrame'に表形式でまとめます。

  * charOnlyがtrueの場合、特性X線データのみを表示します（エスケープなどは含まれません）。
  * `material`がMaterialの場合、計算されたk比（KCalc）もkmeas/kcalc（KoKCalc）と共に表形式でまとめられます。
  * columns - オプションの列出力を選択します（以下を参照）

列：

  * Spectrum : UnknownLabel - フィットスペクトルを識別します
  * Feature  : Label - フィット特徴を識別します（Vector{CharXRay}またはその他）
  * Reference: String - :Spectrumが:Featureに対してフィットした参照の名前
  * K : Float64 - 乗法フィット定数
  * dK : Float64 - :Kの1σ不確かさ
  * :Start : Int - フィットチャネルの開始インデックス（:roi ∈ columns）
  * :Stop : Int - フィットチャネルの停止インデックス（:roi ∈ columns）
  * :Counts : Float64 - 特性ピーク（ピークバック）内の総カウント（:peakback || :counts ∈ columns）
  * :Back : Float64 - 特性ピーク下の背景内の総カウント（:peakback ∈ columns）
  * :PtoB : Float64 - 10 eV/チャネルを仮定したピーク対背景（:peakback ∈ columns）
  * :KCalc : Float64 - 組成を仮定した計算されたk比。（`material`引数を指定する必要があります。）
  * :KoKcalc : Float64 - 測定された/計算されたk比の比率。（`material`引数を指定する必要があります。）
  * :LiveTime : Float64 - 取得ライブ時間（秒）（:dose ∈ columns）
  * :ProbeCurrent : Float64 - プローブ電流（nA）（:dose ∈ columns）
  * :DeadPct : Float64 - ProbeCurrent内のデッドタイム（:dose ∈ columns）
  * :RefCountsPernAs : Float64 - :Feature内の:Referenceにおける単位線量あたりの推定カウント。（:counts ∈ columns）
  * :CountsPernAs : Float64 - :Feature内の:Spectrumにおける単位線量あたりの推定カウント。（:counts ∈ columns）
