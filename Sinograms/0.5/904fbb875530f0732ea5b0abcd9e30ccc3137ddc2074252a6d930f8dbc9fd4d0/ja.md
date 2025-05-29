```
image = fdk(plan, proj)
```

円形ソース軌道を介して収集されたコーンビームコンピュータトモグラフィー（CBCT）データからFDK法を使用して3D画像を再構成します。

# 入力

  * `plan::FDKplan`
  * `proj` (ns,nt,na) 投影ビュー

# 出力

  * `image` (nx,ny,nz) 再構成された画像

参考文献: Feldkamp, Davis, Kress, JOSA-A, 1(6):612-9, 1984年6月。
