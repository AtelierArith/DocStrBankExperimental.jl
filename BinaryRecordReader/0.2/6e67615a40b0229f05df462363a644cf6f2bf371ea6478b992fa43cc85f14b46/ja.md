```
construct_reader_deep(S,array_specs)
```

`Base.read(io::IOStream, ::Type{S})` メソッドを生成します。このメソッドは、`isbitstype` ではない型 `S` を読み取るために使用できます。問題のクラスに他の非 `isbitstype` から構成されるフィールドがある場合、`array_spec` に完全な仕様を設定する必要があります。`types` の構文は `SubTypeName__fieldname` です。

# 例

```julia-repl
julia> struct C
            lat::Float32
            time::Matrix{Int32}
        end
julia> struct B
            fun::UInt8
            funMat::Matrix{UInt16}
        end
julia> struct A
            long::Float32
            COG::UInt16
            funky::AnotherSimpleRecMat
            data::Matrix{SimpleRecMat}
        end

julia> construct_reader_deep(A, (data=(5,5), B__funMat=(2,2), C__time =(3,3)))

```

上記は、定義された3つの型すべてに対して3つの `read` メソッドを生成します。

関連情報: `construct_reader_shallow`, `@construct_reader`
