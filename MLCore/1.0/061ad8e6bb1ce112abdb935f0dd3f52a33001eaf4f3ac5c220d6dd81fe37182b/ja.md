```
getobs(data, [idx])
```

観測インデックス `idx` に対応する観測を返します。

インデックス `idx` は整数で、範囲は `1:numobs(data)` です。型はオプションで `idx` が整数の配列をサポートできます。

`data` に `getobs` が定義されていない場合、`Tables.table(data) == true` の場合は位置 `idx` の行を返し、それ以外の場合は `data[idx]` を返します。

カスタムデータコンテナの著者は、`getobs` の代わりにその型のために `Base.getindex` を実装するべきです。`getobs` は、`getobs` と `Base.getindex` の間に違いがある型（多次元配列など）に対してのみ実装されるべきです。

返される観測は、いくつかの学習アルゴリズムにそのまま渡すことを意図した形式であるべきです。この「実際のデータ」がどのように見えるべきかについての厳密なインターフェース要件はありません。カスタムデータコンテナの背後にいるすべての著者は、この決定を自分で行うことができます。出力は、`idx` がスカラーの場合とベクターの場合で一貫性があるべきです。

`getobs` はデフォルトで、配列、タプル、名前付きタプル、および辞書のネストされた組み合わせをサポートします。

`getobs` からの返り値は常に具現化されたオブジェクトであるべきで、ビューではなく、元のデータへの参照である可能性があります。

引数 `idx` が提供されていない場合、`getobs(data)` はデータの具現化されたバージョンを返すべきです。

[`getobs!`](@ref) および [`numobs`](@ref) も参照してください。

# 例

```jldoctest
julia> x = (a = [1, 2, 3], b = rand(6, 3));

julia> getobs(x, 2) == (a = 2, b = x.b[:, 2])
true

julia> getobs(x, [1, 3]) == (a = [1, 3], b = x.b[:, [1, 3]])
true

julia> x = Dict(:a => [1, 2, 3], :b => rand(6, 3));

julia> getobs(x, 2) == Dict(:a => 2, :b => x[:b][:, 2])
true

julia> getobs(x, [1, 3]) == Dict(:a => [1, 3], :b => x[:b][:, [1, 3]])
true

julia> struct DummyDataset end

julia> MLCore.numobs(d::DummyDataset) = 10

julia> MLCore.getobs(d::DummyDataset) = [1:10;] 

julia> MLCore.getobs(d::DummyDataset, i::Int) = 0 < i <= numobs(d) ? i : throw(ArgumentError("Index out of bounds"))
```
