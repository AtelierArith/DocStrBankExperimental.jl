```
get_looptransfer(sys, ap::AnalysisPoint; kwargs)
get_looptransfer(sys, ap_name::Symbol; kwargs)
```

分析点 `ap` での（線形化された）ループ伝達関数を計算します。`ap.out` から `ap.in` への伝達関数です。

!!! info "負のフィードバック"
    フィードバックループはしばしば負のフィードバックを使用し、この場合に計算されたループ伝達関数には負のフィードバックが含まれます。標準的な分析ツールは、負のゲインが組み込まれていないループ伝達関数を前提とすることが多く、この関数の結果は使用前に否定する必要があるかもしれません。


# 引数:

  * `kwargs`: `ModelingToolkit.linearize` に送信されます。

関連情報としては [`get_sensitivity`](@ref)、[`get_comp_sensitivity`](@ref)、[`open_loop`](@ref) があります。
