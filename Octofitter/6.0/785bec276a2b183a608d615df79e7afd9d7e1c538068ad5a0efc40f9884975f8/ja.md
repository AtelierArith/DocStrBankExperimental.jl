```
HGCAInstantaneousLikelihood(;gaia_id=1234,N_ave=1)
```

モデルHipparcos-Gaiaカタログの加速度（Brandt et al）データを簡略化された瞬時モデルを使用してモデル化します - 1からNのエポックでの固有運動と位置を計算し、それらを平均化します。これは、各エポックで線形最小二乗解をフィッティングする必要がある完全な`HGCALikelihood`よりも迅速です。HipparcosまたはGaiaミッション中に強い加速度がないシステムに対しては、完全に同等であるべきです。

最初のロード時に、HGCAカタログのeDR3バージョンのダウンロードを受け入れるように求められます。
