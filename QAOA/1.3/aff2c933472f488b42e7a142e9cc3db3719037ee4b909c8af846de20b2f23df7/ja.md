```
expectation(S::Vector{<:Vector{<:Real}}, h::Vector{<:Real}, J::Matrix{<:Real})
```

### 入力

  * `S::Vector{<:Vector{<:Real}}`: すべてのスピンベクトルのベクトル。
  * `h::Vector{<:Real}`: 局所的な磁場のベクトル。
  * `J::Matrix{<:Real}`: 結合行列。

### 出力

  * 提供されたスピン配置に対応するエネルギー期待値。

### 注意事項

  * 平均場近似では、エネルギー期待値は次のように定義されます。

    $$
    \langle E \rangle = - \sum_{i=1}^N \bigg[ h_i + \sum_{j>i} J_{ij}  n_j^z(p) \bigg] n_i^z(p).
    $$

```
