```
AvgCutPruningAlgo <: AbstractCutPruningAlgo
```

信頼度が低いカットを削除します。信頼度は、カットが使用された回数 `nused` とそれを用いて行われた最適化の回数 `nwith` にボーナスを加えたもので、次のように計算されます: nused / nwith + ボーナス。カットが使用されたと見なされるのは、その双対値がゼロでない場合です。このカットがこのカットを使用して問題によって与えられた試行を使用して生成された場合、ボーナスは `mycutbonus` に等しくなります。もし `nwidth` がゼロの場合、`nused/nwith` は `newcuttrust` に置き換えられます。
