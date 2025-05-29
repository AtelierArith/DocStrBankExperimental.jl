```julia
function distances(metric :: Metric,
                      means  :: ℍVector,
                      𝐏      :: ℍVector;
                imeans  :: Union{ℍVector, Nothing} = nothing,
                scale   :: Bool = false,
                ⏩      :: Bool = true)
```

通常、この関数は[`predict`](@ref)関数によって呼び出されるため、必要ありません。

  * k 個のエルミート行列を保持する [ℍVector](https://marco-congedo.github.io/PosDefManifold.jl/dev/MainModule/#%E2%84%8DVector-type-1) $𝐏$ と *z* 行列平均を保持する ℍVector `means` が与えられた場合、$𝐏$ の各行列と `means` の平均との*距離の二乗*を返します。

距離の二乗は、選択された `metric` に従って計算されます。`metric` は [Metric](https://marco-congedo.github.io/PosDefManifold.jl/dev/MainModule/#Metric::Enumerated-type-1) 型です。サポートされている距離関数の詳細については [metrics](https://marco-congedo.github.io/PosDefManifold.jl/dev/introToRiemannianGeometry/#metrics-1) を参照してください。

距離の計算は、`means` における平均の逆を保持する ℍVector がオプションのキーワード引数 `imeans` として渡された場合、フィッシャー計量に最適化されています。他の計量の場合、この引数は無視されます。

`scale` が true の場合（デフォルト）、距離は $𝐏$ の行列のサイズで割られます。これは、異なる次元の多様体上で計算された距離を比較するのに役立ちます。ここでは効果はありませんが、良いプラクティスとして使用されます。

`⏩` が true の場合、距離はマルチスレッドを使用して計算されます。ただし、Julia に指示されたスレッド数が <2 または <3k の場合は除きます。

結果は、距離の二乗の *z*x*k* 行列です。
