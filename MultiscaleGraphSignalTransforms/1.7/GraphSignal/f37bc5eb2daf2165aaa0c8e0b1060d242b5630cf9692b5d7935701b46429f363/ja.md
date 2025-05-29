```
function Adj2InvEuc(G::GraphSig)
```

与えられた GraphSig オブジェクト 'G' のバイナリ重み（隣接）行列を使用して、逆ユークリッド距離行列を持つ GraphSig オブジェクト 'GInvEuc' を生成します。

### 入力引数

  * `G::GraphSig`: GraphSig オブジェクト

### 出力引数

  * `G::GraphSig`: 逆ユークリッド重みを持つ GraphSig オブジェクト
