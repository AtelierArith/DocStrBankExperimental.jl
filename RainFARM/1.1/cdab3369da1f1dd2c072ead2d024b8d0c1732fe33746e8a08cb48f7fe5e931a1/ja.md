```
rf = downscale_spaceonly(r,f,weight=1.;fglob=false, fsmooth=false )
```

メタガウススペクトルフィールド `f` を使用して降水フィールド `r` をダウンスケールします。オプションの重み配列を指定できます。降水はグローバルに保存することができます（`fglob`）または畳み込みを使用して（`fsmooth`）。
