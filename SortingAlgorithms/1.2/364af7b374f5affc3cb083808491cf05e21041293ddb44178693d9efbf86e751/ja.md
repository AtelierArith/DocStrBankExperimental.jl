```
コンブソート
```

ソート関数がコンブソートアルゴリズムを使用することを示します。コンブソートは、コレクションを複数回走査し、間隔を置いて要素のペアを整列させます。間隔は指数関数的に減少し、1になると全体の入力に対して挿入ソートに切り替わります。

特徴:

  * *安定性なし* 同じ値を比較する要素の順序を保持しません（例: 大文字と小文字を区別しない文字のソートにおける "a" と "A"）。
  * *インプレース* メモリ内で行います。
  * *並列化可能* 多くの独立した比較を行うため、SIMD命令を使用したベクトル化に適しています。
  * *病的な入力* `repeat(1:5.0, 4^8)` のような入力は、このアルゴリズムの性能を非常に悪化させる可能性があります。
  * *`n log n` の平均実行時間* 100百万までの長さのランダム入力に対して測定されますが、非常に長い入力に対しては理論的な実行時間は `Θ(n^2)` です。

## 参考文献

  * Dobosiewicz, Wlodzimierz, (1980). "An efficient variation of bubble sort", Information Processing Letters, 11(1), pp. 5-6, https://doi.org/10.1016/0020-0190(80)90022-8.
  * Werneck, N. L., (2020). "ChipSort: a SIMD and cache-aware sorting module. JuliaCon Proceedings, 1(1), 12, https://doi.org/10.21105/jcon.00012
  * H. Inoue, T. Moriyama, H. Komatsu and T. Nakatani, "AA-Sort: A New Parallel Sorting Algorithm for Multi-Core SIMD Processors," 16th International Conference on Parallel Architecture and Compilation Techniques (PACT 2007), 2007, pp. 189-198, doi: 10.1109/PACT.2007.4336211.
