```
@add_batch batch cmd
```

与えられたバッチに通常のRedPitaya関数を追加し、直接評価するのではなく、追加します。

関連情報としては、[`ScpiBatch`](@ref)、[`push!`](@ref)、[`execute!`](@ref)があります。

# 例

```julia
julia>  execute!(rp) do b
          @add_batch b serverMode!(rp, CONFIGURATION)
        end
```
