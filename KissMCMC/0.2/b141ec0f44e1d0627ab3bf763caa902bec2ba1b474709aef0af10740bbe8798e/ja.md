```
squash_walkers(thetas, accept_ratio, blobs, logdensities;
                                                     drop_low_accept_ratio=false,
                                                     drop_fact=2,
                                                     verbose=true,
                                                     order=false, # trueの場合、サンプルは順序付けられます。これはベクトルに格納されていないブロブでは機能しない可能性があります。
                                                     merge_blobs!=append!) # 一つのブロブを別のブロブにマージする関数 (blobs1, blobs1) -> blobs2をblobs1にマージ
```

すべてのemceeウォーカのサンプルを一つのベクトルにまとめます。

これは、低い受け入れ比率を持つウォーカをドロップすることもできます（これはemceeで発生する可能性がありますが、これが大丈夫かどうかは全く確信がありません）、drop*low*accept*ratio=trueを設定することで。 drop*fact -> より多くのウォーカをドロップするために増加させます。

返すもの:

  * thetas
  * mean(accept_ratio[walkers2keep])
  * log-densities
  * blobs
