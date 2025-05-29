マルコフ連鎖 `mc` のサンプルパスを1つシミュレートします。結果のベクトルは、`mc` の状態値のインデックスを要素として持ちます。

### 引数

  * `mc::MarkovChain` : MarkovChain インスタンス。
  * `ts_length::Int` : シミュレーションの長さ
  * `;init::Int=rand(1:n_states(mc))` : 初期状態

### 戻り値

  * `X::Vector{Int}` : サンプルパスを含むベクトルで、長さは ts_length
