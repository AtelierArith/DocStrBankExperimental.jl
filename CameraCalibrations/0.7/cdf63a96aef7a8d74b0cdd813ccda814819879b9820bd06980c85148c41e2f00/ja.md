```
キャリブレーション(files, n_corners, checker_size, extrinsic_index)
```

キャリブレーションオブジェクトを構築します。`files`はチェッカーボードの画像ファイルです。`n_corners`はチェッカーボードの各辺のコーナーの数のタプルです。`checker_size`はチェッカーの物理的なサイズ（例：cm単位）です。`with_distortion`は、モデルに放射状レンズ歪みが含まれるかどうかを制御します。
