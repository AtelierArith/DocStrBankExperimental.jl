```
assign_taxonomy(seq_fasta,ref_fasta; k = 8, n_bootstrap = 100,keep_lp = false,lp=false)
```

DNA配列データに基づいて分類学的分類を割り当てるために、[RDP Naive Bayesian Classifierアルゴリズム](https://pubmed.ncbi.nlm.nih.gov/17586664/)を使用します。この関数は、ターゲットシーケンスと参照データベースを含む2つのfastaファイル`seq_fasta`と`ref_fasta`（のパス）を受け取り、ターゲットシーケンスID、ターゲットシーケンス、分類学的分類、およびブートストラップ信頼レベルを含む`Tables.jl`互換の`ClassificationResult`を返します。

  * `seq_fasta`: 分類されるシーケンスのfastaへのパス。
  * `ref_fasta`: fasta参照データベースへのパス。
  * `k`: 使用するkmersの長さ。
  * `n_bootstrap`: 実行するブートストラップ反復の数。
  * `keep_lp`: `true`の場合、分類結果とともに対数確率の配列を返します。
  * `lp`: 分類器が使用する対数確率の配列。

`ref_fasta`はDADA2形式の参照データベースでなければなりません。例については[こちら](https://benjjneb.github.io/dada2/training.html)を参照してください。
