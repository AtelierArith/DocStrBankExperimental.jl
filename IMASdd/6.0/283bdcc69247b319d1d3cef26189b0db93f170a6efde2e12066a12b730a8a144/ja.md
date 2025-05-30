```
Base.resize!(@nospecialize(ids::IDSvector{T}), condition::Pair{String}, conditions::Pair{String}...; wipe::Bool=true, error_multiple_matches::Bool=true) where {T<:IDSvectorElement}
```

条件が満たされていない場合にサイズを変更します。

`wipe=true` の場合、条件に一致するエントリが見つかった場合、対応する IDS の内容は空になります。

いずれにせよ、IDS は条件で満たされます。

注意: `error_multiple_matches` は条件に一致するすべての追加エントリを削除します。

選択された IDS を返します。
