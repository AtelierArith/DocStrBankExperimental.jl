```
mri_filename(fstring::String, checkdisk::Bool=true)
```

有効なファイル名、ファイル幹、およびファイル拡張子を返します。`fstring`はファイル名またはファイル幹のいずれかであることができます。

有効な拡張子は：mgh、mgz、nii、nii.gzです。したがって、ファイル名はstem.{mgh、mgz、nii、nii.gz}の形式であることが期待されます。

`fstring`がファイル名である場合、幹と拡張子は`fstring`から決定されます。

`fstring`がファイル幹であり、`checkdisk`がtrue（デフォルト）である場合、ファイル名と拡張子は、`fstring`.{mgh、mgz、nii、nii.gz}という名前のファイルをディスク上で検索することによって決定されます。可能な拡張子はこの順序で検索されます。該当するファイルが見つからない場合、空の文字列が返されます。
