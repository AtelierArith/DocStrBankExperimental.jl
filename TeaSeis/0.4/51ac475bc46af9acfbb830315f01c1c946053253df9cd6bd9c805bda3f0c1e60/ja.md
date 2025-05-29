```
fold(io, idx...)
```

フレームのフォールドを計算します。ここで、idxはフレーム/ボリューム/ハイパーキューブのインデックスです。例えば、3Dデータセットの場合は`fold(jsopen("file.js"),1)`、4Dデータセットの場合は`fold(jsopen("file.js",1,2))`、5Dデータセットの場合は`fold(jsopen("file.js"),1,2,3)`です。
