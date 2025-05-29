```
核のギロ磁気比をHz/Tで返すか、コヒーレンスの有効ギロ磁気比を計算します。これは、個々のギロ磁気比とそのコヒーレンス次数の積に等しいです。

定義されていない場合は`nothing`を返します。

# 例

```

jldoctest julia> gyromagneticratio(H1) 2.6752218744e8

julia> gyromagneticratio(SQ(H1)) 2.6752218744e8

julia> gyromagneticratio(MQ(((H1,1),(C13,1)))) 3.3480498744e8

julia> gyromagneticratio(MQ(((H1,0),))) 0.0

```

詳細は[`Nucleus`](@ref)、[`Coherence`](@ref)を参照してください。
```
