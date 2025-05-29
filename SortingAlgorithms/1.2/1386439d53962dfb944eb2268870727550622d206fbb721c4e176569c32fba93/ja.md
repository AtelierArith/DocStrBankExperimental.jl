```
PagedMergeSort
```

ソート関数はページ付きマージソートアルゴリズムを使用する必要があることを示します。ページ付きマージソートは、異なるマージルーチンを使用して、サイズO(√n)のスクラッチスペースで安定したソートを実現するマージソートです。大きなサブ配列をマージするためのマージルーチンは、サイズO(√n)のページをほぼインプレースでマージし、その後ページテーブルを使用して再配置します。スクラッチスペースが十分に大きい深い再帰レベルでは、通常のマージが使用され、1つの入力がスクラッチスペースにコピーされます。スクラッチスペースが完全なサブ配列を保持できるほど大きい場合、入力は両側からインターリーブされてマージされ、ランダムデータのパフォーマンスが向上します。

特徴:

  * *安定*: 等しいと比較される要素の順序を保持します（例: 大文字と小文字を無視した文字のソートにおける "a" と "A"）。
  * *`O(√n)`* 補助メモリ使用量。
  * *`O(n log n)`* 確実な実行時間。

## 参考文献

  * Dvořák, S., Ďurian, B. (1986). Towards an efficient merging. In: Gruska, J., Rovan, B., Wiedermann, J. (eds) Mathematical Foundations of Computer Science 1986. MFCS 1986. Lecture Notes in Computer Science, vol 233. Springer, Berlin, Heidelberg. https://doi.org/10.1007/BFb0016253
  * https://max-arbuzov.blogspot.com/2021/10/merge-sort-with-osqrtn-auxiliary-memory.html
