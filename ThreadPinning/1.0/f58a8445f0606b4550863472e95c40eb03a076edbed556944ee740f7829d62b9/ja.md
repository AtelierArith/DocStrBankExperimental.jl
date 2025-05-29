OpenBLASスレッドのアフィニティを指定されたCPUスレッドに設定します。

*例:*

  * `openblas_setaffinity_cpuids(socket(1))` # 最初のソケットにアフィニティを設定
  * `openblas_setaffinity_cpuids(numa(2))` # 2番目のNUMAドメインにアフィニティを設定
  * `openblas_setaffinity_cpuids(socket(1, 1:3))` # 最初のNUMAドメインの最初の3つのコアにアフィニティを設定
  * `openblas_setaffinity_cpuids([1,3,5])` # IDが1、3、5のCPUスレッドにアフィニティを設定。
