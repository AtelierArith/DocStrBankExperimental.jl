```
is_well_formed(aux::AbstractAuxiliary) -> Bool
```

補助が正しく形成されているかを確認します。`AbstractAuxiliary`は、データが不正である2つの方法を区別します：データが破損していてキーやキー/値ペアの値のエンコードされたデータの開始/終了を特定できない場合、補助は不正であると言います。このような補助に対して値にアクセスしたり、反復処理を行ったりすると、例外がスローされる場合とされない場合があります。この不正の概念が、この関数がチェックするものです。

また、キーとエンコードされた値を特定できるが、エンコードされた値が破損していて値をロードできない場合、補助は無効であると言います。このような補助は反復処理が可能で、値をロードできますが、ロードされた値は[`XAMAuxData.Error`](@ref)型になります。これは`isvalid`で確認できます。有効な補助は常に正しく形成されています。

# 例

```jldoctest
julia> aux = SAM.Auxiliary("KM:i:252\tAK::C"); # 不正なキー

julia> is_well_formed(aux)
false

julia> aux["KM"] # 値のロードはエラーになる可能性があります
252

julia> aux["AK"] # 値のロードはエラーになる可能性があります
ERROR: Invalid SAM tag header. Expected <AuxTag>:<type tag>:, but found no colons.
[...]

julia> aux = SAM.Auxiliary("AB:Z:αβγδ\tCD:f:-1.2"); # 不正な値のエンコーディング

julia> (is_well_formed(aux), isvalid(aux))
(true, false)

julia> aux["AB"] # 注意：列挙の数値値はAPIではありません
InvalidString::Error = 9
```
