```
merge(a::SeisBlock{DT}, b::SeisBlock{DT};
           force::Bool = false, consume::Bool = false) where {DT<:Union{IBMFloat32, Float32}}
```

`blocks`、`SeisBlock`オブジェクトのベクターを1つの`SeisBlock`オブジェクトにマージします。

デフォルトでは、`merge`は各`SeisBlock`が一致するファイルヘッダーを持っていることを確認します。これにより、返される`SeisBlock`がそのファイルヘッダーと一貫性があることが保証されます。このチェックは、`force`キーワードを使用してオフにすることができます。falseに設定すると、`merge`はファイルヘッダーのメタデータを確認せずに`blocks`を結合しようとします。`blocks`の最初のファイルヘッダーが返される`SeisBlock`のファイルヘッダーとして使用されます。

デフォルトでは、`merge`はトレースヘッダーを参照しますが、`blocks`の要素からデータをコピーします。メモリ使用量が懸念される場合、`consume`キーワードを使用すると、コピーされた後に各`block`のトレースヘッダーとデータフィールドがクリアされます。これにより、メモリ内のデータの重複を防ぐことができますが、`blocks`の要素がクリアされるコストがかかります。

# 例

```
julia> s = segy_scan(joinpath(dirname(pathof(SegyIO)),"data/"), "overthrust", ["GroupX"; "GroupY"], verbosity = 0);

julia> a = s[1:4]; b = s[5:8];

julia> c = merge([a; b]);

julia> c.traceheaders[1] === a.traceheaders[1]
true

julia> c = merge([a; b], consume = true);

julia> a.traceheaders
0-element Array{SegyIO.BinaryTraceHeader,1}
```
