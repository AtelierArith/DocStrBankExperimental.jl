```julia
struct ExodusPostProcessor{Exo<:Exodus.ExodusDatabase} <: Cthonios.AbstractPostProcessor
```

  * `exo::Exodus.ExodusDatabase`
  * `solution_fields::Vector{String}`

Exodusポストプロセッサは、`Exodus.jl`を介してエクソダスファイルにノード、要素、および四分点フィールドなどの量を書き込むためのものです。 `exo` - 開いているエクソダスデータベースへのハンドル。 `solution_fields` - ノード上のソリューションフィールドの名前のベクトルです。
