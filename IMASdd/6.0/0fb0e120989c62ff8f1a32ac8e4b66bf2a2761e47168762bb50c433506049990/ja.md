```
resize!(
    @nospecialize(ids::IDSvector{T}),
    identifier_name::Symbol,
    conditions::Pair{String}...;
    wipe::Bool=true,
    error_multiple_matches::Bool=true
)::T where {T<:IDSvectorElement}
```

`identifier_name` が `index_2_name(ids)` の `index` に基づいて見つからない場合、条件が満たされていない場合に ids をリサイズします。

wipe=true の場合、条件に一致するエントリが見つかった場合、対応する IDS の内容は空になります。

いずれにせよ、IDS は条件で満たされます。

注意: `error_multiple_matches` は条件に一致するすべての追加エントリを削除します。

選択された IDS を返します。
