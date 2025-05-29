```
monitorloglikelihood!(monitor, rbm, epoch, datadict)
```

`datadict`のデータセットの対数尤度をRBMモデル`rbm`でAISを用いて推定し、推定量の分散に関する情報と共に`monitor`に値を格納します。

利用可能なワーカーが複数ある場合、計算はデフォルトで並列化されます。並列化はオプションのブール引数`parallelized`でオンまたはオフにできます。

他のオプションのキーワード引数については`aislogimportanceweights`を参照してください。

参照: `loglikelihood`。
