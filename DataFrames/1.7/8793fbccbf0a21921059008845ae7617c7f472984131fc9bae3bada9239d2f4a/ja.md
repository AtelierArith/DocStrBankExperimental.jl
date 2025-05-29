```
copy(dfr::DataFrameRow)
```

[`DataFrameRow`](@ref) と同じ内容の `NamedTuple` を構築します。このメソッドは `NamedTuple` を返すため、返されたオブジェクトは `dfr` がビューである親データフレームの変更の影響を受けません。
