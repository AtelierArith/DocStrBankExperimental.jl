MPIHaloArray

# フィールド

  * `data`: AbstractArray{T,N} - 現在のランクのローカルデータを含む
  * `partitioning`: パーティショニングデータ型
  * `comm`: MPIコミュニケーター
  * `window`: MPIウィンドウ
  * `neighbor_ranks` : Vector{Int} - 隣接する配列/MPIプロセスのID
  * `coords` : Vector{Int} - グローバルMPI空間内の座標
  * `rank`: 現在のMPIランク
