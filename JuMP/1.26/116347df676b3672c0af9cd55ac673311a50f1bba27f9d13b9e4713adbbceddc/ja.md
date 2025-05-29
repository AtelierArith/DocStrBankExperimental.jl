```
anonymous_name(::MIME, x::AbstractVariableRef)
```

印刷時に匿名変数 `x` に使用する名前。

## 例

```jldoctest
julia> model = Model();

julia> x = @variable(model);

julia> anonymous_name(MIME("text/plain"), x)
"_[1]"
```
