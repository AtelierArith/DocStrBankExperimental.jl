```
record_output(f, filepath::AbstractString, start_time::Float64=time(); delay=0, kw...) -> filepath
record_output(f, io::IO=IOBuffer(), start_time::Float64=time(); delay=0, kw...)
```

`f()`を実行し、すべての出力を`io`に保存されるキャスト、または`filepath`にあるファイルに保存します。引数`kw...`は、[`Header`](@ref)によって受け入れられる任意のキーワード引数である可能性があります。

キャストのパラメータはここで渡すことができます。詳細については、[`Cast`](@ref)を参照してください。

`Cast`オブジェクトを返します。
