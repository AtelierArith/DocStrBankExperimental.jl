```
mutable struct TessOutput{T}
    result::Union{T, Nothing}
end
```

パイプラインに出力レンダラーを追加したときに返される出力オブジェクト。このオブジェクトは通常、[`tess_run_pipeline`](@ref) メソッドが完了するまで `nothing` を保持します。

また、次を参照してください: [`tess_pipeline_text`](@ref)
