```
segments                = meanshift(img, spatial_radius, range_radius; iter=50, eps=0.01))
```

画像をmeanshiftクラスタリングを使用してセグメント化します。`SegmentedImage`を返します。

パラメータ：

  * img                            = 入力グレースケール画像
  * spatial*radius/range*radius    = 切断正規カーネルのバンド幅パラメータ。カーネルのサイズを制御することで、モード検出の解像度が決まります。
  * iter/eps                       = meanshift手法の停止基準。アルゴリズムは、iter回の反復後、またはカーネル中心が更新ステップでeps距離未満移動した場合のいずれか早い方で停止します。
