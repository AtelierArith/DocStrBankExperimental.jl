```julia
load_hdf5(filename; polarization, style)

```

HDF5ムービーファイルを読み込みます。`filename`はHDF5ファイルである必要があります。

# 詳細

これはHDF5ムービーファイルを読み込み、VIDAMovieオブジェクトを出力します。`polarization=true`の場合、すべてのストークスパラメータを読み込みます。

# 注意

現在、これは*ehtim*によって作成されたムービーでのみ動作します。
