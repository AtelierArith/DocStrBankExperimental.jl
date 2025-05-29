```
correct_background!(xdata::AbstractVector{<:Real}, ydata::AbstractVector{<:Real}, type::Background, offset::Bool=true)::Nothing
```

`ydata` と `xdata` の背景補正を `type` の補正を使用して行います。`offset` が `true`（デフォルト）の場合、`ydata` はその最小値が 0 になるようにシフトされます。
