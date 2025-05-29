```
is_invalid_startvalue(result::TrackerResult)
```

開始値が無効であったためにパス追跡が失敗した場合、`true`を返します。正確な戻りコードを取得するには`result.return_code`を調べることができます。`is_invalid_startvalue(result) == true`の場合の可能な値は次のとおりです。

  * `:terminated_invalid_startvalue_singular_jacobian`は、提供された開始値でのホモトピーのヤコビ行列が特異であることを示します。つまり、フルカラムランクを持っていない場合です。
  * `:terminated_invalid_startvalue`は、提供された開始値がホモトピーの解に十分近くないことを示します。
