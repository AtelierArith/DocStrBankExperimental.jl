```
islabelenc(obj, encoding) -> Bool
```

与えられたオブジェクト `obj` が、指定された `encoding` によって生成されたと説明できるかどうかをチェックします。この場合、関数は true を返し、そうでない場合は false を返します。

```
julia> islabelenc([1,0,1], LabelEnc.ZeroOne)
true

julia> islabelenc([1,-1,1], LabelEnc.ZeroOne)
false
```
