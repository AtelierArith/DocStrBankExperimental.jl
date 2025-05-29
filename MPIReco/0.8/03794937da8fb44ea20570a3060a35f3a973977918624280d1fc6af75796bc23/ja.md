```
getMeasurementsMotionCompFD(bMeas::MPIFile, motFreq, tmot, freq, frames, sigma,
                  samplingPrecision, windowType)
同じ動作状態に対応する生データの平均を取り、仮想フレームを作成します
```

  * bMeas:		Measデータ
  * motFreq:		各パッチとフレームのための主要な動作周波数を含む配列
  * tmot:			同じ状態の繰り返しを含む配列（フレーム、パッチ、周期）
  * freq:			再構成のために選択された周波数
  * frames:       選択されたフレーム
  * alpha:        DFサイクルに対するウィンドウ幅。
  * samplingPrecision:	true: サンプリング精度に丸める動作周期、false: DF周期精度に丸める
  * window:		1: ハンウィンドウ、2: FT1A05、3: 矩形
