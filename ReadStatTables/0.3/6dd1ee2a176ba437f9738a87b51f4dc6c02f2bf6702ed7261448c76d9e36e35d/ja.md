```
ReadStatTable{Cols} <: Tables.AbstractColumns
```

`Tables.jl`互換のカラムテーブルで、`ReadStat` Cライブラリを使用して処理されたStata、SAS、またはSPSSファイルから読み取ったデータを収集します。ファイルレベルおよび変数レベルのメタデータは、`DataAPI.jl`に互換性のあるメソッドを介して取得および変更できます。[`readstat`](@ref)によって構築された`ReadStatTable`の場合、`Cols`はデータファイルの解析に複数のスレッドが使用されるかどうかに応じて、`ReadStatColumns`または`ChainedReadStatColumns`のいずれかです。[`writestat`](@ref)のために構築された`ReadStatTable`の場合、`Cols`は任意の`Tables.jl`互換のテーブルのカラムテーブルタイプであることが許可されています。含まれているメタデータについては、[`ReadStatMeta`](@ref)および[`ReadStatColMeta`](@ref)も参照してください。
