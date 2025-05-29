```
MonteCarloMeasurement
```

すべての `MonteCarloMeasurement` のインターフェースを提供する抽象型です。

!!! warning
    ### 必要なインターフェース関数

    次の *関数* **は** 各新しい `MonteCarloMeasurement` に対して `methods` が定義されている必要があります。

      * [`push!`](@ref): 新しい測定値を `MonteCarloMeasurement` インスタンスに移動します。


!!! note
    ### デフォルトインターフェース関数

    次の *関数* は、任意の `MonteCarloMeasurement` に対してデフォルトの `method` を持っています。

      * [`name`](@ref): 与えられた `MonteCarloMeasurement` インスタンスの `name` を定義します。
      * [`measurement`](@ref): [`Measurements.jl`](https://github.com/JuliaPhysics/Measurements.jl) から測定値を構築します。

