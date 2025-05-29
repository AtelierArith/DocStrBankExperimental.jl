```julia
TreePush(str_id::Union{Ptr{Int8}, String})

```

~ Indent()+PushID(). すでにTreeNode()によってtrueを返すときに呼び出されていますが、必要に応じて自分でTreePush/TreePopを呼び出すことができます。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L677).
