CartesianTopology

CartesianTopology型は、隣接情報、現在のランクなどを保持します。

# フィールド

  * `comm`: MPIコミュニケータオブジェクト
  * `nprocs`: 総プロセッサ数（グローバル）
  * `rank`: 現在のランク
  * `coords`: グローバル空間の座標、すなわち `(0,1,1)`
  * `global_dims`: グローバルドメインの次元、すなわち `(4,4)` は4x4のグローバルドメイン
  * `isperiodic`: Vector{Bool}; 各次元の周期性、すなわち `(false, true, true)` はyとzが周期的であることを意味します
  * `neighbors`: OffsetArray{Int}; 隣接ランク（コーナーを含む）、インデックスは `[[ilo, center, ihi], i, j, k]`
