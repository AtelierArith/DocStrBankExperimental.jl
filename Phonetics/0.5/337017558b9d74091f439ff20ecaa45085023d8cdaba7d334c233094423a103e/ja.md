```
VowelSpace(formants::Formants; temporalNorm=true)
```

`formants`に基づく`VowelSpace`のコンストラクタ。この関数は正確な実装ではありませんが、母音空間と母音空間密度の計算に関する詳細については、Story & Bunton (2017, Vowel space density as an indicator of speech performance, *J. Acoust. Soc. Am. 141*(5), EL458-EL464)を参照してください。

# 引数

  * `formants` `VowelSpace`（および対応する密度）を作成するための`Formants`オブジェクト
  * `temporalNorm`（キーワード）密度カウントを`formants`の離散時間ステップ数で割るフラグ。異なる長さの録音間で発生する時間的な違いを考慮し、密度カウントに影響を与えます。

# 戻り値

計算された母音空間と密度を表す`VowelSpace`オブジェクト。
