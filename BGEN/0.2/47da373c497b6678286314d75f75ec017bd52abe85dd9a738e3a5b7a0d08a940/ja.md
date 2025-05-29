```
probabilities!(b::Bgen, v::BgenVariant; T=Float32, clear_decompressed=false)
```

`Bgen`構造体と`BgenVariant`を与えられた場合、確率を計算します。結果は`v.genotypes.probs`内に格納され、`clear!(v)`を使用してクリアできます。

  * T: 結果の型
  * `clear_decompressed`: 実行後に`true`に設定されている場合、解凍されたバイト文字列をクリアします。
