```
next!(p::Union{Progress, ProgressUnknown}; step::Int = 1, options...)
```

`step` 単位の進捗が達成されたことを報告します。最後の更新からの時間間隔に応じて、表示が変更される場合とされない場合があります。

オプションで、表示の `color` を変更することができます。`update!` も参照してください。
