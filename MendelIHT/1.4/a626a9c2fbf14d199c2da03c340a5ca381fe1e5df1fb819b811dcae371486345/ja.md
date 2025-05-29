```
simulate_correlated_snparray(s, n, p; block_length, hap, prob)
```

相関のあるSnpArrayをシミュレートします。SNPはブロックに分けられ、各隣接SNPは確率probで同じになります。ブロック間には相関はありません。

# 引数:

  * `n`: サンプル数
  * `p`: SNPの数
  * `s`: 現在のディレクトリに作成されるSnpArrayの名前（メモリマップ）。メモリマップを使用しない場合は`undef`を使用します。

# オプションの引数:

  * `block_length`: 各LDブロックの長さ
  * `hap`: 各ブロックのためにシミュレートするハプロタイプの数
  * `prob`: 隣接するSNPが同じである確率`prob`。
