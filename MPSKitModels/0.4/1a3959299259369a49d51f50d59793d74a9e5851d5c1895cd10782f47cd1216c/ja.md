```
struct LocalOperator{T,G}
```

`N`体演算子は、タイプ `G` の格子点を通じてインデックス付けされた `N` サイトに作用します。この演算子は、各々が単一のサイトに作用する `MPOTens, instantiate_operatoror` のベクトルとして表現されます。

# フィールド

  * `opp::Vector{T}`: MPO によって表現された `N` 体演算子。
  * `inds::Vector{G}`: `N` サイトインデックス。
