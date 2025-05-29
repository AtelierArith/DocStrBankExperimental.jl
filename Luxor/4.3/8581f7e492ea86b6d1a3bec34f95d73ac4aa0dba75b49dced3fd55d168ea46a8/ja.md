```
box(pt, width, height, cornerradius, action=:none)
box(pt, width, height, cornerradius; action=:none)
```

点 `pt` を中心に、`width` と `height` のボックス/長方形を描き、各コーナーを `cornerradius` で丸めます。

構築されたパスは、弧と直線で構成されています。
