`UnmeasuredElementRule` メカニズムは、フィッティングプロセスに未測定要素を追加するためのルールを実装する方法を提供します。例としては、元素ごとの化学量論や元素ごとの差異があります。

`UnmeasuredElementRule` の実装には、以下のメソッドを含める必要があります：

```
NeXLUncertainties.compute(uer::<:UnmeasuredElementRule, inp::Dict{Element,<:AbstractFloat})::Dict{Element,AbstractFloat}
isunmeasured(uer::<:UnmeasuredElementRule, elm::Element)::Bool
```
