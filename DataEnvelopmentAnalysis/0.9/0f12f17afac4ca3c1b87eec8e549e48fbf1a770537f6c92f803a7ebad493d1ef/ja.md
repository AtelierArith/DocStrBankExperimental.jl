```
deabigdata(X, Y)
```

データ包絡分析を使用して、入力Xと出力Yのビッグデータ放射モデルを計算します。

# オプション引数

  * `orient=:Input`: 放射状の入力モードを選択します。放射状の出力モデルを選択するには、`:Output`を選択します。
  * `rts=:CRS`: 定常的な規模の利益を選択します。変動する規模の利益を選択するには、`:VRS`を選択します。
  * `atol=1e-6`: DMUが効率的と見なされるための許容誤差。
  * `names`: 意思決定単位の名前を含む文字列のベクトル。
