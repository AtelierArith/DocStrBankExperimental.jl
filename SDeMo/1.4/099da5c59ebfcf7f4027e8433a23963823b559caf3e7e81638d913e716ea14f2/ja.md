```
StrictVarianceInflationFactor{N}
```

変数を1つずつ削除し、最大VIFが`N`（浮動小数点数）より小さくなるまで続けます。`VarianceInflationFactor`とは対照的に、この変数選択のアプローチはモデルの交差検証を行わず、他の変数選択手法よりもはるかに悪いモデルになる可能性があります。
