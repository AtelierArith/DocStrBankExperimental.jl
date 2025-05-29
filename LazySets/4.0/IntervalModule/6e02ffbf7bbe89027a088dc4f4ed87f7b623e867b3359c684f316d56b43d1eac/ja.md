```
chebyshev_center_radius(x::Interval; [kwargs]...)
```

区間の[チェビシェフ中心](https://en.wikipedia.org/wiki/Chebyshev_center)と対応する半径を計算します。

### 入力

  * `x`      – 区間
  * `kwargs` – その他のキーワード引数（無視されます）

### 出力

ペア `(c, r)` で、`c` は `x` のチェビシェフ中心、`r` は `c` を中心とした最大のユークリッド球の半径で、`x` に含まれています。

### 注意事項

区間のチェビシェフ中心は単に区間の中心です。 ```
