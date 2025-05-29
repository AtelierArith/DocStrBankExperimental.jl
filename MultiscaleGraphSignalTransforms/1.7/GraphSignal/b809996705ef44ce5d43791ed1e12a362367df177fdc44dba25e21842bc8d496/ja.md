```
function ggrid(Nx::Int, Ny::Int, connect::Symbol)
```

2-DグリッドのGraphSigオブジェクトを生成します。サイズは`Nx` x `Ny`です。

### 入力引数

  * `Nx::Int`: x方向のポイント数
  * `Ny::Int`: y方向のポイント数
  * `connect::Symbol`: 2-Dグリッドの接続モードを指定します。選択肢は: :c4 (デフォルト), :c8, :full

### 出力引数

  * `G::GraphSig`: 2-D `Nx` x `Ny`グリッドを表すGraphSigオブジェクトです。
