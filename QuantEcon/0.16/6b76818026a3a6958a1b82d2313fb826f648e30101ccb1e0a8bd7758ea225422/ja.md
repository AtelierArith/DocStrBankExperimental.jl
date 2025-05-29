`mc`のマルコフ連鎖の1つのサンプルパスをシミュレートします。結果のベクトルは、`mc`の状態値を要素として持ちます。

### 引数

  * `mc::MarkovChain` : MarkovChainインスタンス。
  * `ts_length::Int` : シミュレーションの長さ
  * `;init::Int=rand(1:n_states(mc))` : 初期状態

### 戻り値

  * `X::Vector` : 長さts_lengthのサンプルパスを含むベクトル
