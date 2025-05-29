```
StackFrameCategory(modcat=FlameGraphs.default_modcat,
                   loccat=FlameGraphs.default_loccat,
                   colorbg=colorant"white",
                   colorfont=colorant"black")
```

スタックフレームをそのカテゴリに基づいて色付けします。

`modcat(mod::Module)` はスタックフレームのモジュールに基づいて色を返すべきであり、モジュールに基づいてスタックフレームを分類できない場合は `nothing` を返します。

`loccat(sf::StackFrame)` は色を返さなければなりません。スタックフレームの任意のフィールドを使用できますが、`func`、`file`、`line`、および `from_c` が一般的な選択肢かもしれません。

`colorbg` は背景色であり、`colorfont` はフォント色の選択を格納します。

# 例

```julia
using Plots, Profile, FlameGraphs
@profile plot(rand(5))    # "最初のプロットまでの時間"
g = flamegraph(C=true)
img = flamepixels(StackFrameCategory(), g)
```

または、自分で色付けを調整することもできます：

```julia
function modcat(mod)
    mod == Plots && return colorant"purple"
    return nothing
end
img = flamepixels(StackFrameCategory(modcat), g)
```
