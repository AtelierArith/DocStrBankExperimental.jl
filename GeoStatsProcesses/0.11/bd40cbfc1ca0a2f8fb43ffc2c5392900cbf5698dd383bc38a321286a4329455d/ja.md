```
LUSIM()
```

Alabert 1987年とDavis 1987年によって導入されたLUシミュレーション法。

完全な共分散行列はデータのすべての位置を含むように構築され、多変量ガウス分布からのサンプルは下三角行列と上三角行列（LU）による行列因子分解を通じて引き出されます。

## 参考文献

  * Alabert 1987. [共分散行列のLU分解による迅速な条件付きシミュレーションの実践](https://link.springer.com/article/10.1007/BF00897191)
  * Davis 1987. [共分散行列のLU三角分解による条件付きシミュレーションの生成](https://link.springer.com/article/10.1007/BF00898189)
  * Oliver 2003. [ガウス共シミュレーション：クロス共分散のモデル化](https://link.springer.com/article/10.1023%2FB%3AMATG.0000002984.56637.ef)

### 注意事項

この方法は、比較的小さな要素数（例：100x100グリッド）を持つドメインにのみ適しており、完全な共分散を因子分解することが可能です。

より大きなドメイン（例：3Dグリッド）では、[`SEQSIM`](@ref)や[`FFTSIM`](@ref)などの他の方法が好まれます。
