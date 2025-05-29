```
VarianceInflationFactor{N}
```

変数を1つずつ削除し、最大VIFが`N`（浮動小数点数）より小さくなるまで、またはモデルの性能が向上しなくなるまで続けます。結果として得られる変数のセットは、しきい値よりも大きな最大VIFを持つ場合があります。代替手段として`StrictVarianceInflationFactor`を参照してください。
