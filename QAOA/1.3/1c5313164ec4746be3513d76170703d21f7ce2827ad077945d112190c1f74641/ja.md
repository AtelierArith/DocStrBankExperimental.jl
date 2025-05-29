```
evolve!(S::Vector{<:Vector{<:Vector{<:Real}}}, h::Vector{<:Real}, J::Matrix{<:Real}, β::Vector{<:Real}, γ::Vector{<:Real})
```

### 入力

  * `S::Vector{<:Vector{<:Vector{<:Real}}}`: すべてのスピンベクトルのベクトルの空の履歴。
  * `h::Vector{<:Real}`: 問題のハミルトニアンの局所磁場のベクトル。
  * `J::Matrix{<:Real}`: 問題のハミルトニアンの結合行列。
  * `β::Vector{<:Real}`: QAOAドライバーパラメータのベクトル。
  * `γ::Vector{<:Real}`: QAOA問題パラメータのベクトル。

### 出力

  * 入力の `S` は、完全な平均場AOA進化の後、すべてのスピンベクトルのベクトルの完全な履歴となります。

### 注意事項

  * これは `evolve` の第二のディスパッチであり、スピンベクトルのベクトルの完全な履歴を返します。
  * サイズ `num_layers = size(β)[1]` のスケジュールの場合、`S` は次のように初期化できます。

    `S = [[[1., 0., 0.] for _ in 1:num_qubits] for _ in 1:num_layers+1]`。
