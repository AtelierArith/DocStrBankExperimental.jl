```
unfold_spectrum(spect::DataSample, n::Int) → unfolded::UnfoldedSpectrum
```

`spect`の展開されたスペクトルを、状態の統合密度に対して次数`n`の多項式をフィッティングすることによって返します。

## 引数

  * `n` : 統合密度の滑らかな部分をモデル化する多項式の次数。
