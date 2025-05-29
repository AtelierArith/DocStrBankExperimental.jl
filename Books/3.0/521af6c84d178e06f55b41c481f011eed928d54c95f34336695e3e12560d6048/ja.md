```
entr_gen(
    path::Union{AbstractString,Regex},
    [block_number];
    M=[],
    kwargs...
)
```

`contents`内のファイルやモジュール`M`のいずれかのコードが変更されるたびに、`gen(path, [block_number]; M, kwargs...)`を実行します。これは`Revise.entr(() -> gen(...), ["contents"], M)`の便利な関数です。

# 例

```
julia> entr_gen("plots"; M=[MyModule])
[...]

julia> entr_gen(r"plot*"; M=[MyModule])
[...]
```
