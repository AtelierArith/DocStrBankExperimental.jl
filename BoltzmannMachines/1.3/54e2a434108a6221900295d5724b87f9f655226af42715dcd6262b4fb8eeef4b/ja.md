```
monitorlogproblowerbound!(monitor, dbm, epoch, datadict)
```

`datadict`のデータセットの対数確率の下限をDBM `dbm`でAISを用いて推定し、推定量の分散に関する情報と共に`monitor`に値を格納します。

利用可能なワーカーが複数ある場合、計算はデフォルトで並列化されます。並列化はオプションのブール引数`parallelized`でオンまたはオフにできます。

他のオプションのキーワード引数については`aislogimpweights`を参照してください。

参照: `logproblowerbound`。
