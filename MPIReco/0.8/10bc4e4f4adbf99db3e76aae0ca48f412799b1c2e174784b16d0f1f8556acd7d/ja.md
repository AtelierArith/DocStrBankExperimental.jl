```
reconstructionPeriodicMotion(bSF::MPIFile, bMeas::MPIFile, freq::Array{Int64,1};
			bEmpty=nothing, bgFrames=nothing,
			alpha::Float64=3.0, choosePeak::Int64=1, frames::UnitRange=1:acqNumFrames(bMeas),
			samplingPrecision::Bool=true, windowType::Int64=1,
			bSFFrequencyAnalysis::MPIFile=bSF,higherHarmonic::Int64=1,
			kargs...)

周期的な動きを持つオブジェクトからの生データのマルチパッチ再構成を実行します
```

  * bSF:			再構成のためのシステム関数
  * bMeas:		測定の生データ
  * freq:                 再構成のために選択された周波数
  * bEmpty:		背景測定
  * bgFrames:		背景フレーム
  * choosePeak:		動作周波数のために選択されたピークの数
  * alpha:        	DFサイクルに対するウィンドウ幅
  * frames: 		選択されたフレーム
  * lambda:		再構成のための正則化パラメータ
  * iterations:		反復の数
  * samplingPrecision:    true: サンプリング精度に丸めた動作周期、false: DF周期精度に丸める
  * windowFunction:       1: ハンウィンドウ、2: FT1A05、3: 矩形
  * bSFFrequencyAnalysis: 周波数分析のためのシステム関数
