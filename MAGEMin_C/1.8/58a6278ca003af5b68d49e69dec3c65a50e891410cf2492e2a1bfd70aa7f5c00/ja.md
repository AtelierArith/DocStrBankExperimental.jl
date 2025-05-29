```
Dat = Initialize_MAGEMin(db = "ig"; verbose::Union{Bool, Int64} = true)
```

データベース `db` に対して、1つ以上のスレッドでMAGEMinを初期化します。すべての出力を抑制するには `verbose=false` を使用します。 `verbose=true` は結果の簡単な要約を提供し、 `verbose=1` は計算に関するより詳細な情報を提供します。
