```
WindowVect{V} <: AbstractWindowShape
```

ユーザー指定のウィンドウベクトルで、`WindowVect(v::V)`を介して構築され、ここで`v`は`AbstractVector`です。注意: `length(v)`はパディングされたシノグラムサイズに適切でなければなりません。
