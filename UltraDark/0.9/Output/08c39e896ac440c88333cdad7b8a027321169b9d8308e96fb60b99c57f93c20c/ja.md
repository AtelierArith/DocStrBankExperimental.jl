```julia
struct OutputConfig
```

出力する情報を含む構造体です。

出力形式は2つの可能性があります：

  * numpyの形式を使用する.npファイル。これらは[`NPZ`](https://github.com/fhs/NPZ.jl)で読み取ることができます。
  * [`HDF5`](https://github.com/JuliaIO/HDF5.jl)で読み取ることができるHDF5ファイルです。

`summary_statistics`の各メンバーは、`t`、`a`、`Δt`および`grids`オブジェクトから要約統計を生成するコンストラクタを持つ別の構造体である必要があります。これが[`PencilGrids`](@ref)オブジェクトと一緒に使用される場合、各フィールドは具体的であり、MPIが処理できるバイナリ表現を持っている必要があります。

デフォルトでは、`summary_statistics`は壁時間とシミュレーション時間のみを書き込みます。

# フィールド

  * `directory::String`: 出力を書き込む場所
  * `output_times::Array{Float64}`: 出力する時刻
  * `box::Bool`: ボックスを出力するかどうか
  * `slice::Bool`: スライスを出力するかどうか
  * `psi::Bool`: ψを出力するかどうか
  * `rho::Bool`: ρを出力するかどうか
  * `npy::Bool`: .npyファイルを書き込む
  * `h5::Bool`: HDF5ファイルを書き込む
  * `summary_statistics::Tuple`: 収集する要約統計のタイプ
