`X`にマルコフ連鎖`mc`のサンプルパスを列として埋めます。結果の行列は、`mc`の状態値を要素として持ちます。

### 引数

  * `X::Matrix` : マルコフ連鎖`mc`のサンプルパスで埋めるための事前割り当てされた行列

`X`の要素の型は、`mc`の状態値の型と同じである必要があります。

  * `mc::MarkovChain` : MarkovChainインスタンス。
  * `;init=rand(1:n_states(mc))` : 次のいずれかである可能性があります。

      * 空白: 各連鎖のためのランダムな初期条件
      * スカラー: 各連鎖のための同じ初期条件
      * ベクター: 要素を循環させ、各要素を初期条件として適用し、すべての列に初期条件が設定されるまで続ける（初期条件よりも多くの列を持つことを可能にします）
