```
pix2zphiNest(res::Resolution, pix) -> (z, phi)
```

ピクセル番号 `pix` の中心の角度座標 `z = cos(θ), ϕ` を計算します。これはピクセルの `NEST` 番 numbering スキームを仮定しています。*注意:* このメソッドは、高解像度で極近くでは不正確です。
