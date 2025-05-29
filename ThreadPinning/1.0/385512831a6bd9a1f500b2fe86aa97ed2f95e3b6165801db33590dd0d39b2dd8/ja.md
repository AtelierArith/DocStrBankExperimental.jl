Juliaスレッドのアフィニティを指定されたCPUスレッドに設定します。

*例:*

  * `setaffinity(socket(1))` # 最初のソケットにアフィニティを設定
  * `setaffinity(numa(2))` # 2番目のNUMAドメインにアフィニティを設定
  * `setaffinity(socket(1, 1:3))` # 最初のNUMAドメインの最初の3つのコアにアフィニティを設定
  * `setaffinity([1,3,5])` # IDが1、3、5のCPUスレッドにアフィニティを設定。
