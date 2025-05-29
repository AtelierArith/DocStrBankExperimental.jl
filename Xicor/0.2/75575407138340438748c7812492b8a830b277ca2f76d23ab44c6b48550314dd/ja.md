```
xicor(X, Y; rank=tiedrank, noties=false)
```

2つのベクトル `X` と `Y` の間の非対称 ξ 相関係数を計算します。`rank` はランクの計算方法を指定し、デフォルトでは `denserank` を使用します。`Y` に重複がない場合、`noties` を `true` に設定することで計算が高速化されます。

`ξ` はこの関数のエイリアスです。
