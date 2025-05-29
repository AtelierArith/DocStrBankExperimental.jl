`MPIHaloArray`を`root` MPIランクに集めて、つなぎ合わせます。これにより、ハロ領域のデータは無視され、グローバルな状態を表す`Array`が作成されます。

# 引数

  * `A`: MPIHaloArray
  * `root`: `A`を集めるMPIランク
  * `halo_dims`: ハロ交換が行われる次元のタプル（まだ完全には機能していません）
