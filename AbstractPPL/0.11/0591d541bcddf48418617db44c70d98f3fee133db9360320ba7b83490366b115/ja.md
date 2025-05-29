```
varname_to_string(vn::VarName)
```

`VarName`を中間辞書を介して文字列として変換します。これは、具体化されたスライスが忠実に表現される点で`string(vn)`とは異なります（コロンとして美しく表示されるのではなく）。

配列にインデックスを付ける`VarName`に対して、この関数はインデックスがシリアライズ可能な場合にのみ機能します。これはすべての標準Juliaインデックスタイプに当てはまりますが、カスタムインデックスタイプを使用している場合は、それらのタイプに対して`index_to_dict`および`dict_to_index`メソッドを実装する必要があります。これを行う方法については、[`dict_to_index`](@ref)のドキュメントを参照してください。

```jldoctest
julia> varname_to_string(@varname(x))
"{\"optic\":{\"type\":\"identity\"},\"sym\":\"x\"}"

julia> varname_to_string(@varname(x.a))
"{\"optic\":{\"field\":\"a\",\"type\":\"property\"},\"sym\":\"x\"}"

julia> y = ones(2); varname_to_string(@varname(y[:]))
"{\"optic\":{\"indices\":{\"values\":[{\"type\":\"Base.Colon\"}],\"type\":\"Base.Tuple\"},\"type\":\"index\"},\"sym\":\"y\"}"

julia> y = ones(2); varname_to_string(@varname(y[:], true))
"{\"optic\":{\"indices\":{\"values\":[{\"range\":{\"stop\":2,\"type\":\"Base.OneTo\"},\"type\":\"AbstractPPL.ConcretizedSlice\"}],\"type\":\"Base.Tuple\"},\"type\":\"index\"},\"sym\":\"y\"}"
```
