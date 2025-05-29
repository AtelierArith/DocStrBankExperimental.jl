```
HyperSpectrum(arr::Array{T<:Real}, energy::EnergyScale, props::Array{Symbol, Any})

HyperSpectrum(energy::EnergyScale, props::Dict{Symbol,Any}, arr::Array{<:Real}; axisnames = ( "X", "Y", "Z", "A", "B", "C" ), fov = ( 1.0, 1.0, 1.0, 1.0, 1.0, 1.0 ), livetime=)
HyperSpectrum(energy::EnergyScale, props::Dict{Symbol,Any}, arr::AxisArray)
HyperSpectrum(energy::EnergyScale, props::Dict{Symbol,Any}, dims::NTuple{<:Integer}, depth::Int, type::Type{Real}; axisnames = ( "X", "Y", "Z", "A", "B", "C" ), fov = ( 1.0, 1.0, 1.0, 1.0, 1.0, 1.0 )

HyperSpectrum構造体は、Spectrumオブジェクトの多次元配列を表します。HyperSpectrumの次元は、トラバースまたはラインスキャンの場合は1、スペクトル画像の場合は2、またはスペクトル画像のタイムシリーズやマルチスライススペクトル画像の場合は2より大きくなります。

最初のコンストラクタは、生のデータのArrayからHyperSpectrumを作成するために使用されます。2番目は、別のHyperSpectrumまたはAxisArrayからHyperSpectrumを構築するために使用されます。3番目は、意図された内容の説明から作成されます。

  * `axisnames`: 軸を参照するための名前のリスト
  * `fov`: mm単位の次元の全幅。

HyperSpectraは、HyperSpectrum内のスペクトルが:ProbeCurrentや:BeamEnergyのようなプロパティを共有しなければならない点でArray{Spectrum}とは異なります。ただし、各ピクセルは独自のlivetimeを持つことができます。HyperSpectrumオブジェクトは、ラインスキャン（1D）、スペクトル画像（2D）、スライスアンドビュー（3D）、時間順序の画像（3D）、または高次元スペクトル画像を参照できます。

内部的に、HyperSpectrumはArray{T<:Real, N+1}をArray{Spectrum{T<:Real},N-1}として再解釈します。

HyperSpectrumオブジェクトは、RPL/RAWファイルから読み取ることができます（`readrplraw(filenamebase::AbstractString)`を使用）が、任意のArray{<:Real}から構築することもできます。

HyperSpectrumオブジェクトは、単一の整数インデックスやCartesianIndexを含む標準のJulia配列の慣用句を使用してインデックス付けできます。たとえば、HyperSpectrum内のすべてのスペクトルを反復処理するには

```

% 2048チャンネルの[0,255]を持つ21行×19列のスペクトル画像を構築します。 hs = HyperSpectrum{es, props, (21,19), 2048, UInt8} for idx in eachindex(hs)     spec = hs[idx]   % idxでの2048チャンネルのデータを表すSpectrumを取得     spec[22] = 1     % 22番目のチャンネルを1に設定 end % HyperSpectrumへのインデックスは(row, column)です ```
