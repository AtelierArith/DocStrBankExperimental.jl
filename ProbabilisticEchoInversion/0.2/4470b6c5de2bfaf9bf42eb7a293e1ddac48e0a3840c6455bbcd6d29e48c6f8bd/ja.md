```
iterspectra(echogram[, freqdim])
```

多周波数または広帯域のエコーグラムが `DimArray` の形式で与えられ、音響周波数が1次元にある場合（デフォルトでは `:F` と名付けられています）、各スペクトルを反復処理します。イテレータは、次の3つのフィールドを持つ `NamedTuples` を生成します：

  * `coords`: 配列の非 `:F` 次元におけるスペクトルの座標（すなわち、その位置空間/時間）
  * `freqs`: 音響周波数の配列
  * `backscatter`: バックスキャッタ値の配列
