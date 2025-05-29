```
HDF5Logger
```

HDF5ファイルにデータのフレームをログするためのオブジェクトを作成します。フレームは同じサイズであることが期待され、ログするフレームの総数は事前に知られている必要があります。現在、HDF5パッケージがサポートする基本的な型のスカラー、ベクトル、および行列で動作します。

# 例 1: 時間に沿ったベクトルのログ

```julia
log = Log("my_file.h5") # ロガーを作成します。
num_frames = 100        # ログするフレームの総数を設定します。
example_data = [1., 2., 3.] # データのフレームの例を作成します。
add!(log, "/a_vector", example_data, num_frames) # ストリームを作成します。
log!(log, "/a_vector", [4., 5., 6.]) # 単一のデータフレームをログします。
log!(log, "/a_vector", [7., 8., 9.]) # 次のフレームをログします。
close!(log) # 終了時には必ずクリーンアップします。try-catchを使用して確認してください。

# 通常のHDF5ライブラリを使用して読み戻します。
using HDF5
x = HDF5.h5open("my_file.h5", "r") do logs
    read(logs, "/a_vector")
end
```

# 例 2: 時間に沿ったスカラーのログ

基盤となるHDF5ライブラリ（HDF5.jl）は、物事を配列としてログするため、スカラーを渡すとHDF5ファイル内に1-by-nの配列が生成され、n長のベクトルにはなりません。`squeeze`を使用することでn長のベクトルを取得できます。例えば：

```julia
log = Log("my_file.h5") # ロガーを作成します。
add!(log, "/a_scalar", 0., 1000) # 1000サンプルのスペースを持つストリームを作成します。
log!(log, "/a_scalar", 0.1) # 単一のデータフレームをログします。
log!(log, "/a_scalar", 0.2) # 次のフレームをログします。
close!(log) # 終了時には必ずクリーンアップします。try-catchを使用して確認してください。

# 通常のHDF5ライブラリを使用して読み戻します。
using HDF5
t = HDF5.h5open("my_file.h5", "r") do logs
    read(logs, "/a_scalar")
end # tは現在1-by-1000の配列です。
t = squeeze(t, 1) # n要素のベクトルを作成します。
```

# 注意事項

`add!`の直後に`log!`を行う必要があることが多いため、`add!`関数は便利のためにその例のデータを最初のフレームとしてログすることもできます。次のように使用します：

```julia
add!(log, "/group/name", data, num_frames, true) # ストリームを追加; データをログします。
```
