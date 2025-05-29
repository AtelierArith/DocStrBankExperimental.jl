```
(ins::INS)(ind = trues(ins.N);
           err::Real   = 0.0,
           lat::Vector = [zero(ins.lat[ind]);],
           lon::Vector = [zero(ins.lon[ind]);])
```

特定のインデックスで慣性航法システムデータを取得します。ゼロに設定される可能性があります。

**引数:**

  * `ins`: `INS` 慣性航法システム構造体
  * `ind`: （オプション）選択されたデータインデックス
  * `err`: （オプション）追加の位置誤差 [m]
  * `lat`: （オプション）初期真緯度 [rad]
  * `lon`: （オプション）初期真経度 [rad]

**戻り値:**

  * `ins`: `INS` 慣性航法システム構造体 `ind` で
