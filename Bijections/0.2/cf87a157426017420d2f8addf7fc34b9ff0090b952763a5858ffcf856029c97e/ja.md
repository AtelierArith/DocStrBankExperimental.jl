```
Bijection()
```

新しい `Bijection` を構築します。

  * `Bijection{S,T}()` は、タイプ `S` のオブジェクトからタイプ `T` のオブジェクトへの空の `Bijection` を作成します。`S` と `T` が省略された場合、`Bijection{Any,Any}` になります。
  * `Bijection(x::S, y::T)` は、`x` が `y` にマッピングされた新しい `Bijection` を作成します。
  * `Bijection(dict::Dict{S,T})` は、`dict` のマッピングに基づいて新しい `Bijection` を作成します。
  * `Bijection(pair_list::Vector{Pair{S,T}})` は、`pair_list` のキー/値ペアを使用して新しい `Bijection` を作成します。
