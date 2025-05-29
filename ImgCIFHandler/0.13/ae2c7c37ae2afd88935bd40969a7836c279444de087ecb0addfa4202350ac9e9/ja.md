```
imgload(handle,::Val{:HDF};path="/";frame=1)
```

ファイル `handle` から 2D HDF5 画像を読み込み、HDF5 の場所 `path` に位置し、1 から数えてフレーム番号 `frame` のみを返します。
