```
usePlotPackage(plotPackage::String)
```

`ModiaResult.@usingModiaPlot` コマンドによって使用される ModiaPlot パッケージを定義します。すでに ModiaPlot パッケージが定義されている場合は、内部スタックに保存されます（`usePreviousPlotPackage()` で再アクティブ化可能）。

`plotPackage` の可能な値：

  * `"GLMakie"`
  * `"WGLMakie"`
  * `"CairoMakie"`
  * `"PyPlot"`
  * `"NoPlot"`
  * `"SilentNoPlot"`

# 例

```julia
import ModiaResult

ModiaResult.usePlotPackage("GLMakie")

module MyTest
    ModiaResult.@usingModiaPlot

    t = range(0.0, stop=10.0, length=100)
    result = Dict{String,Any}("time" => t, "phi" => sin.(t))

    plot(result, "phi")  # GLMakie をレンダリングに使用
end
```
