```
@construct_reader S array_specs
```

`Base.read(io::IOStream, ::Type{S})` メソッドを生成します。このメソッドは、`isbitstype` ではない型 `S` を読み取るために使用できます。

# 例

```julia-repl
julia> struct CompoundStruct
           long::Float32
           COG::UInt16
           data::Matrix{Float64}
       end
julia> @construct_reader CompoundStruct (data=(10,10),)
```

上記は、`data` フィールドが 10x10 の行列であると仮定して、適切な `read` メソッドを生成します。

関連情報: `construct_reader_deep`, `@construct_reader`
