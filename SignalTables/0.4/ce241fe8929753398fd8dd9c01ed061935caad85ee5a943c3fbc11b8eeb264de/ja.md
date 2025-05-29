```
usePlotPackage(plotPackage::String)
```

コマンド `@usingPlotPackage` によって使用されるプロットパッケージを定義します。すでにプロットパッケージが定義されている場合は、内部スタックに保存されます（`usePreviousPlotPackage()` で再アクティブ化可能）。

`plotPackage` の可能な値：

  * `"PyPlot"`
  * `"GLMakie"`
  * `"WGLMakie"`
  * `"CairoMakie"`
  * `"SilentNoPlot"`

# 例

```julia
using SignalTables
usePlotPackage("GLMakie")

module MyTest
    using SignalTables
    @usingPlotPackage

    t = range(0.0, stop=10.0, length=100)
    result = Dict{String,Any}("time" => t, "phi" => sin.(t))

    plot(result, "phi")  # GLMakie を使用してレンダリング
end
```
