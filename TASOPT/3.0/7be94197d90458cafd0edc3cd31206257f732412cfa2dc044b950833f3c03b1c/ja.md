```
unpack_ac_components(ac)
```

航空機の物理コンポーネントを展開するためのヘルパー関数。

!!! details "🔃 入力と出力"
    **入力:**

      * `ac::aircraft` : 展開する航空機オブジェクト

    **出力:**

      * `parg::AbstractArray{Float64}` : ジオメトリパラメータ
      * `options::Options` : 航空機の構成オプション
      * `fuse::Fuselage` : 胴体パラメータ
      * `fuse_tank::fuselage_tank` : 胴体内の燃料タンクパラメータ
      * `wing::Wing` : 翼オブジェクト
      * `htail::Tail` : 水平安定板オブジェクト
      * `vtail::Tail` : 垂直安定板オブジェクト
      * `landing_gear::LandingGear`: 着陸装置オブジェクト

