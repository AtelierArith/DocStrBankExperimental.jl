```
find_spectra_peaks(s::KmerFrequencySpectra{1})
```

1D k-mer頻度スペクトルの信号に存在するすべてのピークを、持続的ホモロジー法を使用して自動的に検出します。

[`SpectraPeak`](@ref)のベクターを返します。
