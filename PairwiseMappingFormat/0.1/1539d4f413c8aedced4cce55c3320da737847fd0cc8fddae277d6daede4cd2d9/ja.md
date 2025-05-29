```
PAFReader(io::IO; copy::Bool=true)
```

`PAFReader`を構築します。これは、`io`から読み取られた[`PAFRecord`](@ref)のイテレータです。このオブジェクトを反復処理すると、各有効な入力行に対して`PAFRecord`が返され、無効なレコードが見つかった場合には[`ParserException`](@ref)がスローされます。効率のため、補助フィールドはアクセスされるまで検証されません。

`copy`がfalseの場合、*同じ*レコードが各反復で返され、その内容が上書きされます。これにより、各反復ごとのいくつかのアロケーションが削減されますが、古い反復のレコードが保存されている場合には問題を引き起こす可能性があります。

# 例

```jldoctest
julia> reader = PAFReader(open(path_to_paf)); typeof(reader)
PAFReader{IOStream}

julia> typeof(first(reader))
PAFRecord

julia> PAFReader(open(path_to_paf)) do reader
           for record in reader
                println(record.qlen)
           end
       end
301156
299273
288659

julia> PAFReader(open(path_to_paf); copy=false) do reader
           fst = first(reader)
           all(reader) do record
               record === fst
           end
       end
true
```

関連情報: [`PAFRecord`](@ref), [`try_next!`](@ref) ```
