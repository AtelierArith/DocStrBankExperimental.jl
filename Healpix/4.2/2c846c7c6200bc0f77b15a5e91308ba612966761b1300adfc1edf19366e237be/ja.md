```
pix2zphiRing(res::Resolution, pix) -> (z, phi)
```

ピクセル番号 `pix` の中心の角度座標 `z = cos(θ), ϕ` を計算します。これはピクセルの `RING` 番 numbering スキームを仮定しています。*注意:* このメソッドは、高解像度で極に近い場合には不正確です。
