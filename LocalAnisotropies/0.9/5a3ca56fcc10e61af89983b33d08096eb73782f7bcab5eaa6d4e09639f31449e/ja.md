```
LocalSGS(; [paramaters])
LocalSGS(localaniso; [paramaters])
LocalSGS(method, localaniso; [paramaters])
```

Gomez-Hernandezによって1993年に導入された逐次プロセス法です。これは、パスに従って地理空間ドメインのすべての位置を横断し、単純クリギングを使用して近傍内の条件付きガウス分布を近似し、この分布からサンプリングすることによって近傍の中心に値を割り当てます。

## パラメータ

  * `path`         - プロセスパス（デフォルトは`LinearPath()`）
  * `minneighbors` - 最小隣接数（デフォルトは`1`）
  * `maxneighbors` - 最大隣接数（デフォルトは`36`）
  * `neighborhood` - 検索近傍（デフォルトは`:range`）
  * `distance`     - 最近傍を見つけるために使用される距離（デフォルトは`Euclidean()`）
  * `init`         - データ初期化方法（デフォルトは`NearestInit()`）

プロセス`path`の各位置に対して、最大隣接数`maxneighbors`が条件付きガウス分布をフィットさせるために使用されます。隣接は`neighborhood`に従って検索されます。

`neighborhood`は`MetricBall`、シンボル`:range`、または`nothing`であることができます。シンボル`:range`は`MetricBall(range(γ))`に変換され、ここで`γ`はガウスプロセスの変動関数です。`neighborhood`が`nothing`の場合、最近傍が追加の制約なしで使用されます。

## 参考文献

  * Gomez-Hernandez & Journel 1993. [Joint Sequential Simulation of MultiGaussian Fields](https://link.springer.com/chapter/10.1007/978-94-011-1739-5_8)

### 注意事項

  * この方法はさまざまなパラメータに非常に敏感です。基礎となるクリギングモデルで十分な隣接が使用されていることを確認するために注意が必要です。
