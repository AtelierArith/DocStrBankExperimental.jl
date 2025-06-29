```
resample_conserving_flux(new_wave, old_wave, flux, err=nothing, mask=nothing; fill=NaN)
```

フラックス（およびオプションでエラーとマスク）を新しい波長グリッドに再サンプリングし、フラックスを保存します。

# 必要な引数

  * `new_wave::AbstractVector`: フラックスを再サンプリングする新しい1D波長配列。
  * `old_wave::AbstractVector`: フラックスベクトルが現在サンプリングされている元の1D波長配列。
  * `flux::AbstractArray`: 指定された波長でのフラックスを与えるn次元フラックス配列。この配列の最初の軸は`old_wave`の長さと一致する必要があり、他の軸は独立したスペクトルとして扱われます。

# オプションの引数

  * `err::AbstractArray`: 指定された波長でのフラックスのエラーを与えるオプションのn次元エラー配列。この配列のサイズは`flux`のサイズと一致する必要があります。
  * `mask::BitArray`: 特定のフラックス値をマスクするかどうかを示すブール値を含むオプションのn次元マスク配列。この配列のサイズは`flux`のサイズと一致する必要があります。マスクは新しいフラックスの計算には使用されず、代わりに出力マスクは入力マスクがカバーしていたのと同じピクセルをカバーするように再サンプリングされます。

# キーワード引数

  * `fill::Real=NaN`: 元の波長範囲の外にあるビンを埋めるために使用される埋め値。
  * `verbose::Bool=true`: いくつかのビンが元の波長範囲の外にある場合に警告メッセージを印刷するかどうか。

# 戻り値

  * `new_fluxes::AbstractArray`: 出力波長グリッドに再サンプリングされたフラックス。最初の軸は`new_wave`と同じ長さになり、他のすべての軸は元の`flux`配列と同じになります。

# オプションの戻り値

  * `new_errs::AbstractArray`: 入力`err`が提供された場合のみ返されます。これらは出力波長グリッドに再サンプリングされたエラーです。`new_fluxes`と同じサイズになります。
  * `new_mask::BitArray`: 入力`mask`が提供された場合のみ返されます。これらは出力波長グリッドに再サンプリングされた新しいマスク値です。`new_fluxes`と同じサイズになります。

追加の注意事項:

```
- このモジュールは、SpectRes pythonパッケージから適応されました。https://github.com/ACCarnall/SpectRes、
  アダム・カーナルによるものです。スペクトル再サンプリング手順の理論についての説明は、カーナル（2017）を参照してください：https://ui.adsabs.harvard.edu/abs/2017arXiv170505165C/abstract
  この関数は、元のpythonバージョンの`spectres.spectres`関数と同様に動作するはずです。ただし、以下に列挙されたいくつかの
  小さな違いがあります。

- このバージョンは、フラックス配列の最初の軸が波長軸であると仮定する異なる規約を使用しています。
  pythonバージョンの最後の軸ではなく（これはパフォーマンス上の理由から行われました。juliaは列優先であり、
  pythonは行優先です）。

- `mask`引数が追加されており、`flux`および`err`と同じサイズのBitArrayとしてマスクを入力できます。
  マスクは、出力フラックス配列の新しいビンに結合される元のフラックス配列のすべてのビンに沿って`any`操作を行うことによって結合されます。
  つまり、再ビン化されたフラックスを計算するために使用された元のフラックス配列のいずれかのポイントがマスクされていた場合、
  新しいフラックス値もマスクされます。

- 元のpython SpectResパッケージに対するパフォーマンスの改善に注意が払われています。このバージョンは、元のパッケージの
  numba-jittedバージョンよりもさらに高速です。
```
