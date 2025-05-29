```
peval(params, what)
```

与えられたパラメータ `params` のコンテキストで、指定された式を評価します。

`what` が `ModelParam` の場合、その現在の値が返されます。もしそれがリンクで、古くなっている可能性がある場合は、[`update_links!`](@ref) を呼び出します。

`what` が Symbol または Expr の場合、パラメータ名のすべての言及がその値に置き換えられ、式が評価されます。

`what` が他の値である場合、それは変更されずに返されます。

参照: [`Parameters`](@ref), [`@alias`](@ref), [`@link`](@ref), [`ModelParam`](@ref), [`update_links!`](@ref).
