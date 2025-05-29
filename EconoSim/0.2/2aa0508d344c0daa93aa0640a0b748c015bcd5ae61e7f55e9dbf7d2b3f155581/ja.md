```
ニーズ - アクターのニーズを示します。
```

  * usage_priorities::Set{Int64} - 使用優先度のセットです。これに2つ未満の要素が含まれている場合、使用はランダム化されます。
  * wants_priorities::Set{Int64} - 欲求優先度のセットです。これに2つ未満の要素が含まれている場合、欲求の購入はランダム化されます。
  * use::Dict{Tuple{Int64, Blueprint}, Marginality} - アクターが各サイクルで使用するものを示します。キーのタプル内のInt64は優先度を示します。
  * wants::Dict{Tuple{Int64, Blueprint}, Marginality} - アクターが各サイクルで購入しようとするものを示します。
