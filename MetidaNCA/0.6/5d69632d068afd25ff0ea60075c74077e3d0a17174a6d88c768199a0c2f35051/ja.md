```
nca!(data::DataSet{Subj}; adm = :ev, calcm = :lint, intpm = nothing, verbose = 0, warn = true, wm::Bool = false, io::IO = stdout, modify! = identity) where Subj <: AbstractSubject
```

  * `wm` - DataSetメタデータ（`:ncalog`インデックス）に出力を書き込む。

PK/PDデータの非コンパートメント（NCA）分析。
