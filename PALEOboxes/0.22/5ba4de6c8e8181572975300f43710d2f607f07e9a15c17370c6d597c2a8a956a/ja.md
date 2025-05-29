```
get_variable(
    method::AbstractReactionMethod, localname::AbstractString; 
    allow_not_found=false
) -> v
```

`localname`によって単一のVariableReaction `v`を取得します。

`localname`が存在しない場合、`allow_not_found==true`であれば`nothing`を返し、それ以外の場合はエラーになります。
