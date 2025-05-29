```
gmshcuboid(width, height, length, delta)
```

幅（x軸に沿った）`width`、高さ（y軸に沿った）`height`、および長さ（z軸に沿った）`length`の直方体のメッシュを作成します。これらのパラメータをGMSHメッシャーに組み込んだ.geoスクリプトを解析します。

ターゲットエッジサイズは`delta`です。 physical => {"TopPlate", "BottomPlate", "SidePlates", "OpenBox"}の中から指定された直方体の部分のみを抽出して返します。
