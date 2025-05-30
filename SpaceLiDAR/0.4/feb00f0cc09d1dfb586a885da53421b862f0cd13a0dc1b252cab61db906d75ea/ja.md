```
sync(folder::AbstractString, all::Bool=false; kwargs...)
sync(folders::AbstractVector{<:AbstractString}, all::Bool=false; kwargs...)
sync(product::Symbol, folder::AbstractString, all::Bool=false; kwargs...)
sync(product::Symbol, folders::AbstractVector{<:AbstractString}, all::Bool=false; kwargs...)
```

`folder(s)`内の既存のローカルグラニュールのアーカイブを最新のグラニュールと同期します。具体的には、`folder(s)`にまだ存在しないグラニュールについて[`search`](@ref)と[`download`](@ref)を実行し、リストの*最初*のフォルダにダウンロードします。

!!! warning
    syncを使用すると、かなりの量のデータ（TB以上）をダウンロードする可能性があります。


すべてのフォルダが同じ製品のグラニュールを含んでいると仮定します。そうでない場合は、製品をSymbolとして渡してください: [`sync(::Symbol, folders, all)`](@ref)の代わりに。

`all`がfalse（デフォルト）である場合、syncは`folders`内で見つかった最新のグラニュールの日付以降のグラニュールのみを検索します。trueの場合は、すべてのグラニュールを検索します。ICESatのグラニュールはタイムスタンプがないため、この設定に関係なく、syncはまだ存在しない*すべての*ICESatグラニュールをダウンロードしようとします。

任意の`kwargs...`は[`search`](@ref)関数に渡されます。これにより、syncは特定の範囲内のグラニュールのみをダウンロードすることができます。
