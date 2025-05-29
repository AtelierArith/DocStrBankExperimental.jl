```
smplinfo(smpls::AbstractSamples)::SamplingInfo
smplinfo(wf::RDWaveform{T,U})::RDWaveform
```

サンプルのベクトルの配列、または波形の配列からサンプリング情報を取得します。すべての要素は同じサンプリング情報を持っている必要があります。
