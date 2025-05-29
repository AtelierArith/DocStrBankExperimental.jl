```
coupledcov(ch1, ch2, workspace, spectra;
           noiseratios=Dict(), lmax=0) where T
```

# 引数:

  * `ch1::Symbol`: 最初のスペクトルのスペクトルタイプ (すなわち :TT, :TE, :EE)
  * `ch2::Symbol`: 2番目のスペクトルのスペクトルタイプ (すなわち :TT, :TE, :EE)
  * `workspace`: 共分散を扱うためのキャッシュ
  * `spectra`: 信号スペクトル

# キーワード

  * `noiseratios::AbstractDict`: ホワイトノイズに対するノイズスペクトルの比率
  * `lmax=0`: 共分散行列の最大多極モーメント

# 戻り値:

  * `SpectralArray{T,2}`: 共分散行列 (0インデックス)
