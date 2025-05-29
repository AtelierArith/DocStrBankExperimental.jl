```
estimatenoise!(nmrdata)
```

データのrmsノイズレベルを推定し、`:noise`メタデータを更新します。

`Array`のデータに対して呼び出された場合、各アイテムが更新されます。

# アルゴリズム

データは数値順にソートされ、最高および最低の12.5%のデータが破棄されます（これにより75%のデータが残ります）。これらの値は、最大尤度分析を通じて切断されたガウス分布にフィットされます。

対数尤度関数は次のようになります：

$$
\log L(\mu, \sigma) = \sum_i{\log P(y_i, \mu, \sigma)}
$$

個々のデータポイントの尤度は次のようになります：

$$
\log P(y,\mu,\sigma) =
    \log\frac{
        \phi\left(\frac{x-\mu}{\sigma}\right)
    }{
        \sigma \cdot \left[\Phi\left(\frac{b-\mu}{\sigma}\right) -
            \Phi\left(\frac{a-\mu}{\sigma}\right)\right]}
$$

ここで、$\phi(x)$と$\Phi(x)$は標準正規pdfおよびcdf関数です。
