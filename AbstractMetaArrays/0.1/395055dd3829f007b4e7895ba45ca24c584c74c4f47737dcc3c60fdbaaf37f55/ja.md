AbstractMetaArrays.create_metaarray(::Type{MA}, A::AbstractArray, meta=nothing, colmeta=nothing) where {MA<:AbstractMetaArray}

メタデータおよび列メタデータのコンストラクタのためのヘルパー関数で、AbstractMetaArrayの具体的な実装とそれが含むAbstractArrayの具体的な実装を与えます。この関数はメタデータと列メタデータのタプルを返します。メタデータは文字列キーと型`Tuple{Any,Symbol}`の値を持つ辞書です。列メタデータは、MetaArrayに列メタデータがある場合はシンボルキーと型`MetaType`の値を持つ辞書であり、そうでない場合は何も返しません。

注意: メタデータの形式は、文字列キーと型`Tuple{Any,Symbol}`の値を持つ辞書として`MetaType`型によって与えられます。提供された辞書の値が`Tuple{Any,Symbol}`の形式でない場合は、値に`:default`キーを追加することによってこの形式に変換されます。

# 引数

  * `MA`: メタアレイの型。
  * `A`: ラップされる抽象配列。
  * `meta`: 提供されない場合に使用されるデフォルトメタデータ。DictまたはNothingである可能性があります。
  * `colmeta`: 提供されない場合に使用されるデフォルト列メタデータ。DictまたはNothingまたはDictのタプルである可能性があります。

# 戻り値

メタデータと列メタデータを含むタプル。

# 例

```jldoctest   julia> using StaticArrays   julia> create_metaarray(SimpleMetaArray, SVector{3}(1,1,1), Dict("description" => ("test array", :entry)),           Dict("unit" => ("m", :default)))   (Dict("description" => ("test array", :entry)),    Dict(:x => Dict("unit" => ("m", :default)), :y => Dict("unit" => ("m", :default)), :z => Dict("unit" => ("m", :default))))

julia>create_metaarray(SimpleMetaArray, SVector{3}(1,1,1),Dict("description" => ("test array", :entry)),           (Dict("unit" => ("m", :default)),            Dict("unit" => ("km", :default)),            Dict("unit" => ("cm", :default)))) (Dict("description" => ("test array", :entry)),  Dict(:x => Dict("unit" => ("m", :default))),       :y => Dict("unit" => ("km", :default)),       :z => Dict("unit" => ("cm", :default)))   ```
