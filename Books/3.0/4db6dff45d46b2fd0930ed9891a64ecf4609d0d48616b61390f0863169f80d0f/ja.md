```
gen(
    [paths::Vector{String}],
    [block_number::Union{Nothing,Int}=nothing];
    call_html::Bool=true,
    fail_on_error::Bool=false,
    project="default",
    kwargs...
)
```

`_gen/`内のファイルを必要なメソッドを呼び出すことで生成します。これらのメソッドはファイル名によって指定され、そのファイル名に出力されます。これにより、ユーザーはコードブロックをコードに簡単にリンクできます。メソッドを呼び出した後、このメソッドは`call_html == true`の場合にサイトを更新するために`html()`も呼び出します。`kwargs...`は`M`を無視するためのもので、`entr_gen`は`gen`の代替として使用できます。
