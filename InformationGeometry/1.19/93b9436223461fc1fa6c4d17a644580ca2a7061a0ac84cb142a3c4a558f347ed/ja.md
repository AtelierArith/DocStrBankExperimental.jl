```
ModelMap(Map::Function, InDomain::Union{Nothing,Function}, Domain::HyperCube; startp::AbstractVector)
ModelMap(Map::Function, InDomain::Function, xyp::Tuple{Int,Int,Int})
```

モデルマップに関する追加情報を格納するコンテナであり、特にその有効範囲を示します。`Map`は実際のマップ`(x,θ) -> model(x,θ)`です。`Domain`はさまざまなパラメータの範囲を大まかに指定することを可能にする`HyperCube`です。より複雑な境界制約については、すべての出力コンポーネントが有効なパラメータ領域で.≥ 0となるように、関数`InDomain(θ)`を指定できます。あるいは、`InDomain`はブール値の関数でもよく、パラメータ領域の許容される部分で`true`を評価します。

キーワード引数`startp`は、ModelMapに適切なパラメータベクトルを渡すために使用できます。
