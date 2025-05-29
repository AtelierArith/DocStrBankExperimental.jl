```
add_noise!(server::NoisyServer, server_qureg)
```

`NoisyServer`で定義されたノイズモデルに基づいて、量子レジスタ（`server_qureg`）にノイズを追加します。この関数は、単一および複数のノイズモデルの両方をサポートしています。各ノイズモデルについて、`get_noise_model_params`を使用してパラメータを取得し、量子レジスタ内の各キュービットにノイズを適用します。

# 引数

  * `server::NoisyServer`: 適用されるノイズモデルを含む`NoisyServer`インスタンス。
  * `server_qureg`: ノイズが適用される量子レジスタ。

# 例

```julia
server = NoisyServer(noise_model)
server_qureg = QuantumRegister(3)
add_noise!(server, server_qureg)
```
