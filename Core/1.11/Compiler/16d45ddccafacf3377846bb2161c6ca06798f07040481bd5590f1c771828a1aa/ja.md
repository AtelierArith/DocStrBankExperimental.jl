```
info::UnionSplitInfo <: CallInfo
```

もし推論がメソッド検索空間を分割することによって分割することを決定した場合、各分割に対してメソッドルックアップクエリを発行します。この情報は、そのような分割が発生したことを示し、各分割に対応する `MethodMatchInfo` をラップします（`info.matches::Vector{MethodMatchInfo}`）。この情報は、汎用関数への呼び出しでない任意の文に対しては不正です。
