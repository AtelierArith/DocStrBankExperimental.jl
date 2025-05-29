モデルラッパーのための抽象スーパタイプ `Model`、このパッケージの動作を拡張する必要がある場合に便利です。

# `AbstactModel` パラメータへのアクセス

フィールドには `getindex` を使ってアクセスできます：

```julia
model = Model(obj)
@assert model[:val] isa Tuple
@assert model[:val] == model[:val]
@assert model[:units] == model[:units]
```

`val` と `units` の組み合わせたタプルを取得するには、[`withunits`](@ref) を使用します。

親モデルコンポーネントの型名とフィールド名も利用可能です：

```julia
model[:component]
model[:fieldname]
```

## パラメータ値の `Vector` を取得する

`Base` メソッド `collect`、`vec`、および `Array` は `model[:val]` の結果のベクターを返します。他のパラメータフィールドのベクターを取得するには、単にタプルを `collect` します：

```julia
boundsvec = collect(model[:bounds])
```

## Tables.jl インターフェース

すべての `AbstractModel` は Tables.jl インターフェースを定義しています。これは、パラメータとパラメータメタデータを `DataFrame` または CSV に非常に簡単に変換できることを意味します：

```julia
df = DataFrame(model)
```

Tables.rows はすべての `Param` を `NamedTuple` の `Vector` として返します。

テーブルからパラメータでモデルを更新するには、`update!` または `update` を使用します：

```julia
update!(model, table)
```

## `AbstractModel` インターフェース：独自のモデルラッパーを定義する

他のことにも使用するラッパータイプに `ModelParameters.jl` を使用するのが最も簡単かもしれません。これが DynamicGrids.jl が `Ruleset` で行っていることです。インターフェースを拡張するのは簡単で、ほとんどすべては `AbstractModel` から継承することで処理されます。しかし、いくつかの状況では追加のメソッドを定義する必要があります。

`AbstractModel` は `Base.parent` を使用して親モデルオブジェクトを返します。`<: AbstractModel` タイプにフィールド `:parent` を使用するか、`Base.parent` にメソッドを追加します。

カスタム `parent` フィールドを使用する場合、正しいフィールドを設定する [`setparent!`](@ref) および [`setparent`](@ref) のメソッドも定義する必要があります。

複雑な型パラメータを持つ `AbstractModel` には、`ConstructionBase.constructorof` のメソッドが必要な場合があります。

カスタム `show` メソッドを追加しつつパラメータテーブルを印刷するには、次のようにできます：

```julia
printparams(io::IO, model)
```

これで必要なことはすべてです。
