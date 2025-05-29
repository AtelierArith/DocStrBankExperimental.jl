```
FFTSIM(; [options])
```

オリバー1995年とラヴァレック2000年によって導入されたFFTシミュレーションメソッド。

共分散関数は、ファストフーリエ変換の後に周波数領域で摂動されます。ホワイトノイズがスペクトルの位相に追加され、逆フーリエ変換によって実現が生成されます。

データの条件付けは現在、以下の近傍探索オプションを受け入れるクリギングを使用して行われています。

## オプション

  * `minneighbors` - 最小近傍数（デフォルトは`1`）
  * `maxneighbors` - 最大近傍数（デフォルトは`26`）
  * `neighborhood` - 探索近傍（デフォルトは`nothing`）
  * `distance`     - 最近傍を見つけるために使用される距離（デフォルトは`Euclidean()`）

## 参考文献

  * オリバー1995年. [Moving averages for Gaussian simulation in two and three dimensions](https://link.springer.com/article/10.1007/BF02091660)
  * ラヴァレック他2000年. [The FFT Moving Average (FFT-MA) Generator: An Efficient Numerical Method for Generating and Conditioning Gaussian Simulations](https://link.springer.com/article/10.1023/A:1007542406333)
  * フィゲイレド他2019年. [Revisited Formulation and Applications of FFT Moving Average](https://link.springer.com/article/10.1007/s11004-019-09826-4)

### 注意事項

このメソッドは、規則的なグリッド上でのシミュレーションに制限されており、相関長がグリッドサイズに比べて十分に小さいことを確認する必要があります。一般的な目安として、相関長がグリッドの1/3を超えないようにしてください。

相関長がグリッド自体に比べて大きい場合、グリッドの境界近くに視覚的なアーティファクトが現れることがあります。
