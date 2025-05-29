```
plotconf(object; size = (500, 400), cnt = true, ptext = true, 
    fontsize = 15, coldiag = :red, )
```

混同行列をプロットします。

  * `object` : 関数 `conf` の出力。

キーワード引数:

  * `size` : 図のサイズ（横、縦）。
  * `cnt` : ブール値。`true` の場合は出現回数をプロットし、そうでない場合は行の %s をプロットします。
  * `ptext` : ブール値。`true` の場合は各セルの値を表示します。
  * `fontsize` : `ptext = true` のときのフォントサイズ。
  * `coldiag` : `ptext = true` のときのフォントカラー。

関数 `conf` のヘルプページに例があります。 ```
