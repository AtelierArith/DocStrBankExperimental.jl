```
bids_layout(bidsPath::AbstractString;
    derivatives::Bool=true,
    specific_folder::Union{Nothing,AbstractString}=nothing,
    exclude_folder::Union{Nothing,AbstractString}=nothing,
    ses::Union{Nothing,AbstractString}=nothing,
    task::Union{Nothing,AbstractString}=nothing,
    run::Union{Nothing,AbstractString}=nothing)
```

`bids_root`フォルダ内のすべての被験者のパスを読み込むためのメイン関数。特定の被験者情報を含むすべての見つかったパスを含むDataFrameを返します。メモリにデータを読み込む前に[`load_bids_eeg_data`](@ref)を使用します。

## キーワード

  * `derivatives::Bool = true`  派生フォルダ内のデータを探します
  * `specific_folder::Union{Nothing,AbstractString} = nothing`  データを探すために、派生またはbids_root内の特定のフォルダ名を指定します。
  * `exclude_folder::Union{Nothing,AbstractString} = nothing`  データ検出から特定のフォルダを除外します。
  * `ses:Union{Nothing,AbstractString} = nothing`  読み込むセッション; 何も指定しない場合はすべて読み込みます
  * `task::Union{Nothing,AbstractString} = nothing`  読み込むタスク; 何も指定しない場合はすべて読み込みます
  * `run::Union{Nothing,AbstractString} = nothing`  読み込むラン; 何も指定しない場合はすべて読み込みます
