```
get_comp_sensitivity(sys, ap::AnalysisPoint; kwargs)
get_comp_sensitivity(sys, ap_name::Symbol; kwargs)
```

分析点 `ap` における補完感度関数を計算します。補完感度関数は、`ap` の出力に無限小の摂動 `d` を導入し、システムを線形化し、`d` と `ap` の入力との間の伝達関数を計算することによって得られます。

# 引数:

  * `kwargs`: `ModelingToolkit.linearize` に送信されます

関連項目としては [`get_sensitivity`](@ref)、[`get_looptransfer`](@ref) があります。
