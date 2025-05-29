```
imgr = imROF(img, λ, iterations)
```

Rudin-Osher-Fatemi (ROF) フィルタリングを実行します。これは、より一般的には全変動 (TV) ノイズ除去または TV 正則化として知られています。`λ` は導関数の正則化係数であり、`iterations` は行われる緩和反復の回数です。2次元のみ。

詳細は https://en.wikipedia.org/wiki/Total*variation*denoising および Chambolle, A. (2004). "An algorithm for total variation minimization and applications".     Journal of Mathematical Imaging and Vision. 20: 89–97 を参照してください。
