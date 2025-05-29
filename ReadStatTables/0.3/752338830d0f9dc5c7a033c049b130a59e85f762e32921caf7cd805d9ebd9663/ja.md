```
ReadStatTable(table, ext::AbstractString; kwargs...)
```

`ext`の拡張子を持つサポートされているファイル形式のために、`Tables.jl`互換の列テーブルをラップすることによって`ReadStatTable`を構築します。`DataAPI.jl`によって定義された`metadata`および`colmetadata`インターフェースを介して、[`ReadStatMeta`](@ref)または[`ReadStatColMeta`](@ref)のメタデータフィールドに一致するキーを持つテーブルレベルまたは列レベルのメタデータを収集しようとします。

このメソッドは、提供された`table`がすでに`ReadStatTable`でない場合に[`writestat`](@ref)によって使用されます。したがって、書き込む内容を細かく制御するのに役立ちます。メタデータはキーワード引数で手動で指定できます。

文字列列に存在する`missing`は空文字列`""`に置き換えられます。要素型`Missing`の列は空文字列を持つ列として扱われます。

# キーワード

  * `copycols::Bool = true`: データ列を`ReadStatColumns`にコピーします。これは、数値値としてすでに表現されていない日付/時刻値の列を書くために必要です。
  * `refpoolaslabel::Bool = true`: `DataAPI.refpool`を利用する配列型の列に対して値ラベルを生成します（例：`CategoricalArray`および`PooledArray`）。
  * `vallabels::Dict{Symbol, Dict} = Dict{Symbol, Dict}()`: 名前でインデックス付けされたすべての値ラベル辞書の辞書。
  * `hasmissing::Vector{Bool} = Vector{Bool}()`: 対応する列に存在する欠損値があるかどうかのインジケーターのベクター；テーブルを書く際には無関係です。
  * `meta::ReadStatMeta = ReadStatMeta()`: ファイルレベルのメタデータ。
  * `colmeta::ColMetaVec = ReadStatColMetaVec()`: `ReadStatColMeta`の`StructArray`に格納された変数レベルのメタデータ；値は常に上書きされます。
  * `varformat::Union{Dict{Symbol,String}, Nothing} = nothing`: 変数名（`Symbol`として）をキーとし、フォーマット文字列を値とする特定の変数のための変数レベルのフォーマットを指定します。
  * `styles::Dict{Symbol, Symbol} = _default_metastyles()`: メタデータスタイル。
  * `maxdispwidth::Integer = 60`: いかなる変数に対しても設定される最大`display_width`。
