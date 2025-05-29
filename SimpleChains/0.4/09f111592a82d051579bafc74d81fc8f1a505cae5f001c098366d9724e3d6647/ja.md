```
TurboDense{B=true}(activation, outputdim::Integer)
```

線形（密）層。

  * `B` は層がバイアス項を含むかどうかを指定します。
  * `activation` 関数は結果に要素ごとに適用されます。
  * `outputdim` は入力がマッピングされる次元数を示します。

（Xavier）グロロット正規分布を使用して重みをランダムに初期化します。バイアスはゼロ初期化されます。
