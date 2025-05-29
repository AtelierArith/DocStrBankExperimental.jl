```
lobanov(f1, f2, vowel, speaker)
```

ロバノフ正規化ルーチンを実行し、各スピーカーのF1およびF2のzスコアを計算します。詳細については、Lobanov (1971, Classification of Russian vowels spoken by different speakers. J. Acoust. Soc. Am. 49(2B), 606–608) を参照してください。

# 引数

  * `f1`  F1値
  * `f2` F2値
  * `vowel` 母音カテゴリ; 計算には使用されませんが、適切なフォルマントおよびスピーカー情報とリンクさせるために渡されます
  * `speaker` スピーカーIDの`Array`; 整数、シンボル、文字列、および`DataFrames`パッケージの`groupby`関数でサポートされている他のデータ型を使用できます
