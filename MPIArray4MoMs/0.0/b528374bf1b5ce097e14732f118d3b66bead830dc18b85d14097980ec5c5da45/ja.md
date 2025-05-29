```
PatternTransfer{T, I} <: TRANSFER
```

特殊用途のデータ転送を作成し、オクタツリーのレベル内で異なる `rank` 間の放射関数や設定関数のパターン転送データを扱います。

```
parent::MPIArray{T, IA, 3} where {IA}           転送されるパターン `MPIArray`。
reqsIndices::I                                  必要なインデックス
reqsDatas::Dict{Int, SparseMatrixCSC{T, Int}}   SparseMatrixCSCを使用してpoleおよびθϕ方向のデータを保存し、Dictでcubeデータを保存します。
recv_rk2idcs::Dict{Int, I}                      本 `rank` が受信する `rank` およびローカルデータ内のインデックス。
send_rk2idcs::Dict{Int, I}                      本 `rank` が送信する `rank` およびローカルデータ内のインデックス。
```
