いくつかのランタイムパラメータ。デフォルト値は `=` の後にあります。

## ステップ 1:

```julia
bm3d_config.thr_patchSize = CartesianIndex(8, 8)	パッチのサイズ;
bm3d_config.thr_searchStride = CartesianIndex(3, 3)	処理を高速化するために、画像のピクセルに対するループは行と列でステップ（整数）で行われます;
bm3d_config.thr_searchWin = CartesianIndex(19, 19)	検索ウィンドウのサイズ;
bm3d_config.thr_nMatch = 31	保持される類似パッチの最大数;
bm3d_config.thr_thresh3D = 2.7	3Dグループのしきい値;
bm3d_config.thr_distFunction = Euclidean2	ブロック間の距離を測定する関数;
bm3d_config.thr_group_transform! = FFTW.dct!	グループ内で3D変換を行う関数;
bm3d_config.thr_group_itransform! = FFTW.idct!	グループ内で3D逆変換を行う関数;
```

## ステップ 2:

```julia
bm3d_config.wie_patchSize = CartesianIndex(8, 8)	パッチのサイズ;
bm3d_config.wie_searchStride = CartesianIndex(3, 3)	処理を高速化するために、画像のピクセルに対するループは行と列でステップ（整数）で行われます;
bm3d_config.wie_searchWin = CartesianIndex(11, 11)	検索ウィンドウのサイズ;
bm3d_config.wie_nMatch = 15	保持される類似パッチの最大数;
bm3d_config.wie_distFunction = Euclidean2	ブロック間の距離を測定する関数;
bm3d_config.wie_group_transform! = FFTW.dct!	グループ内で3D変換を行う関数;
bm3d_config.wie_group_itransform! = FFTW.idct!	グループ内で3D逆変換を行う関数;
```

## その他

bm3d*config.show*info = false	いくつかの実行メッセージを表示

注:

3Dグループデータ構造:

```
G3D[k, :, :]	# k 番目のマッチングブロック。
size(G3D)	# (nMatch, patchSize[1], patchSize[2])
```
