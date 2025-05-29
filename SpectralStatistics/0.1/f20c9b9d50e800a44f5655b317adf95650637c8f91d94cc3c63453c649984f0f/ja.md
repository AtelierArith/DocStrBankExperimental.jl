```
unfold_spectrum(spect::DataSample, n::Int, cut_values) → unfolded::UnfoldedSpectrum
```

`spect`の展開されたスペクトルを、状態密度の積分に対して次数`n`の多項式を区分的にフィッティングすることによって返します。

## 引数

  * `cut_values` : スペクトルの部分間のカットの相対位置。
