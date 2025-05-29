```
writeAlmToFITS(f::CFITSIO.FITSFile, alm::Alm{Complex{T}}) where {T <: Number}
writeAlmToFITS(fileName, alm::Alm{Complex{T}}; overwrite = true) where {T <: Number}
```

a_ℓm係数のセットをFITSファイルに書き込みます。コードが失敗した場合、CFITSIOは例外を発生させます。（詳細についてはCFITSIOライブラリを参照してください。）fitsファイルでは、almsは明示的なインデックススキームで書き込まれます。$\mathrm{index} = \ell^2 + \ell + m + 1$、順序が異なる可能性があります（`almExplicitIndex`を確認してください）。
