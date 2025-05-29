```
execute!(f::Function, rp::Union{RedPitaya, RedPitayaCluster})
```

`ScpiBatch`を開き、関数`f`を評価します。例外がスローされなかった場合、開かれたバッチを実行します。

詳細は[`ScpiBatch`](@ref)、[`push!`](@ref)、[`@add_batch`](@ref)を参照してください。

# 例

```julia
julia>  execute!(rp) do b
          @add_batch b serverMode!(rp, CONFIGURATION)
          @add_batch b amplitudeDAC!(rp, 1, 1, 0.2)
        end
```
