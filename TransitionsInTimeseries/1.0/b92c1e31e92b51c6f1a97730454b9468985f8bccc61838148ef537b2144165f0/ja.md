```
SlidingWindowConfig <: ChangesConfig
SlidingWindowConfig(indicators, change_metrics; kwargs...)
```

[`estimate_changes`](@ref) に与えることができる設定です。スライディングウィンドウアプローチによって遷移を推定します：

1. 入力時系列に対してウィンドウをスライドさせることで、指標の時系列を推定します。
2. 指標の時系列に対して変化メトリックのウィンドウをスライドさせることで、指標の変化を推定します。

指標と変化メトリックは、`x::AbstractVector` を入力として受け取り、`s::Real` を出力する **汎用のJulia関数** です。任意の関数を指定することができ、最適化の可能性についてはドキュメントの [カスタム指標/変化メトリックの作成](@ref own_indicator) を参照してください。

`indicators` は単一の関数または指標のタプルであることができます。同様に、`change_metrics` もタプルまたは単一の関数であることができます。タプルの場合、`indicators` と `change_metrics` の長さは一致しなければなりません。このようにして、複数の指標および/または変化メトリックに対して効率的に分析を繰り返すことができます。

`SlidingWindowConfig` に対応する結果出力は [`SlidingWindowResults`](@ref) です。

ステップ1は、`indicators` に `nothing` が提供された場合はスキップされ、その場合、変化メトリックは入力データから直接推定されます。

## キーワード引数

  * `width_ind::Int=100, stride_ind::Int=1`: 入力時系列から指標を計算するために [`WindowViewer`](@ref) に与えられる幅とストライド。
  * `width_cha::Int=50, stride_cha::Int=1`: 指標の時系列から変化メトリックの時系列を計算するために [`WindowViewer`](@ref) に与えられる幅とストライド。
  * `whichtime = midpoint`: 指標 / 変化メトリックの時系列に対応する時間ベクトルは、キーワード `whichtime` を使用して [`estimate_changes`](@ref) の `t` から取得されます。オプションには以下が含まれます：

      * `last`: 各ウィンドウの最後の時間点を使用
      * `midpoint`: 各時間ウィンドウの中間時間点を使用
      * `first`: 各ウィンドウの最初の時間点を使用

    実際、指標の時間ベクトルは単純に次のように計算されます。

    ```julia
    t_indicator = windowmap(whichtime, t; width_ind, stride_ind)
    t_change = windowmap(whichtime, t_indicator; width_cha, stride_cha)
    ```

    したがって、`mean` や `median` など、時間ウィンドウの時間点自体を抽出するために他の関数を指定することもできます。
  * `T = Float64`: 一部の計算を初期化するための入力時系列の要素型。
