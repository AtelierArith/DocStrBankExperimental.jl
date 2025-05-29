```
braille(io::IO, H::Union{SparseMPO, MPOHamiltonian})
braille(H::Union{SparseMPO, MPOHamiltonian})
```

スパースMPOまたはMPOハミルトニアンのコンパクトで人間が読みやすい「ブライユ」ビジュアライゼーションを出力します。MPOの各サイトはUnicodeブライユ文字のブロックとして表され、サイトはダッシュで区切られます。このビジュアライゼーションは、MPOの構造とスパースパターンを迅速に検査するのに便利です。

# 引数

  * `io::IO`: 出力先のストリーム（例: `stdout`）。
  * `H::Union{SparseMPO, MPOHamiltonian}`: ビジュアライズする`SparseMPO`または`MPOHamiltonian`。

`io`引数なしで呼び出された場合、出力は`stdout`に印刷されます。
