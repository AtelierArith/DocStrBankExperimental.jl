```
generate_test_problems(datFilename::String, solFilename::String,
    model::Function, modelStr::String, n::Int, np::Int, p::Int;
    x_interval::Tuple{Float64, Float64}=(-10.0, 10.0),
    θSol::Vector{Float64}=10.0 * randn(n), std::Float64=200.0,
    out_times::Float64=7.0)

generate_test_problems(datFilename::String, solFilename::String,
    model::Function, modelStr::String, n::Int, np::Int, p::Int,
    cluster_interval::Tuple{Float64, Float64};
    x_interval::Tuple{Float64, Float64}=(-10.0, 10.0),
    θSol::Vector{Float64}=10.0 * randn(n), std::Float64=200.0,
    out_times::Float64=7.0)
```

フィッティング問題のテスト用のランダムデータファイルを生成します。

  * `datFilename` と `solFilename` は、それぞれランダムデータと解を保存するファイルの名前を持つ文字列です。
  * `model` はモデル関数で、`modelStr` はこのモデル関数を表す文字列です。例えば、

    ```
     model = (x, θ) -> θ[1] * x[1] + θ[2]
     modelStr = "(x, θ) -> θ[1] * x[1] + θ[2]"
    ```

    ここでベクトル `θ` はモデルのパラメータ（見つけるべきもの）を表し、ベクトル `x` はモデルの変数です。
  * `n` はパラメータの数です。
  * `np` は生成されるポイントの数です。
  * `p` はLOVOアプローチで使用される信頼できるポイントの数です。

`cluster_interval` が提供されている場合、この間隔内でのみ外れ値を生成します。

追加のパラメータ：

  * `xMin`, `xMax`: 一次元テストでポイントを生成するための間隔 *非推奨*
  * `x_interval`: 一次元テストでポイントを生成するための間隔
  * `θSol`: 真の解で、摂動ポイントを生成するために使用されます
  * `std`: 標準偏差
  * `out_times`: 外れ値の偏差は `out_times * std` になります。
