MPIHaloArray コンストラクタ

# 引数

  * `A`: AbstractArray{T,N}
  * `topo`: 並列トポロジータイプ、例: CartesianTopology
  * `nhalo`: ハロセルの数

# キーワード引数

  * `do_corners`: [true] コーナーハロ領域を交換する
  * `com_model`: [:p2p] 通信モデル、例: :p2p はポイントツーポイント (Isend, Irecv)、:rma はワンサイド (Get,Put)、:shared は MPI の共有メモリモデル
