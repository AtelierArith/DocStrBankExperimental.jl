SpectrumScaling タイプは、主にプロットのためにスペクトルデータを再スケーリングするように設計されています。

**実装**

```
Base.show(io::IO, scn::SpectrumScaling)
scalefactor(sc::SpectrumScaling, spec::Spectrum)
```
