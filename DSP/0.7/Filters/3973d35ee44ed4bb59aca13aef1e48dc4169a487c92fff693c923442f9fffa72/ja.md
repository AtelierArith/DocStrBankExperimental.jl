```
resample(x, rate[, coef])
```

`x`を有理数または任意の`rate`で再サンプリングします。`coef`はFIRフィルタタップのオプションのベクトルです。`coef`が提供されない場合、タップはカイザーウィンドウを使用して計算されます。

内部的に、`resample`はポリフェーズ`FIRFilter`オブジェクトを使用しますが、信号の再サンプリングを容易にするために追加の操作を行います。`FIRFilter`の遅延（ランプアップ）を補正し、`x`にゼロを追加します。その結果、入力信号と出力信号を重ねてプロットすると、非常によく相関しますが、一方の信号にはもう一方よりも多くのサンプルがあります。
