```
ValidationManifold{𝔽,M<:AbstractManifold{𝔽}} <: AbstractDecoratorManifold{𝔽}
```

関数のインターフェースで定義された入力および出力値にテストを追加するための多様体。

さらに、点と接ベクトルもカプセル化できます。cf. [`ValidationMPoint`](@ref)、[`ValidationTangentVector`](@ref)、および[`ValidationCotangentVector`](@ref)。これらの型は、点と接ベクトルの両方が（プレーン）配列として表される多様体で作業する際に、データがどこから来ると想定されているかを確認するために使用できます。

`ignore_contexts`キーワードを使用すると、無視するコンテキストの単一の`Symbol`または`Symbols`のベクトルを指定できます。

現在のコンテキストは

  * `:All`: すべてのチェックを無効にする
  * `:Point`: 点のチェック
  * `:Vector`: ベクトルのチェック
  * `:Output`: 出力のチェック
  * `:Input`: 入力変数のチェック

`ignore_functions`キーワード（辞書）を使用すると、この多様体内の単一の関数内で特定のチェックを無効にすることができます。辞書の`key`は、何かを除外するための`Function`でなければなりません。`value`は、`ignore_contexts`キーワードと同じ意味を持つ単一のシンボルまたはシンボルのベクトルですが、この関数に限定されます。

# 例

  * `exp => :All`は[`exp`](@ref)関数内の*すべての*チェックを無効にします
  * `exp => :Point`は[`exp`](@ref)関数内の点のチェックを除外します
  * `exp => [:Point, :Vector]`は[`exp`](@ref)関数内の点とベクトルのチェックを除外します

この多様体は多様体のデコレーターであり、すなわち、点、ベクトル、および共ベクトルの型で[`AbstractManifold`](@ref) `M`を装飾します。

# フィールド

  * `manifold::M`: 装飾される多様体
  * `mode::Symbol`: エラーハンドリングに使用されるモード、`:error`または`:warn`
  * `ignore_contexts::AbstractVector{Symbol}`: 検証で無視されるコンテキストを格納します。
  * `ignore_functions::Dict{<:Function,<:Union{Symbol,<:AbstractVector{Symbol}}`: 関数またはその変異バリアント内で無視されるコンテキストを格納します。

# コンストラクタ

```
ValidationManifold(M::AbstractManifold; kwargs...)
```

バリデーション多様体を生成します

```
ValidationManifold(M::AbstractManifold, V::ValidationManifold; kwargs...)
```

デフォルト値の`V`を持つ`M`のためのバリデーション多様体を生成します。

## キーワード引数

  * `error::Symbol=:error`: 検証中のエラーがどのように報告されるべきかを指定します。これは[`is_point`](@ref)および[`is_vector`](@ref)に`error`キーワード引数として渡されます。利用可能な値は`:error`、`:warn`、`:info`、および`:none`です。他のすべての値は`:none`として扱われます。
  * `store_base_point::Bool=false`: 接ベクトルまたは共ベクトルが関連付けられている点`p`を保存するかどうかを指定します。これはデバッグ目的で便利です。
  * `ignore_contexts = Vector{Symbol}()` 検証コンテキストを実行しないことを示すベクトル。
  * `ignore_functions=Dict{Function,Union{Symbol,Vector{Symbol}}}()` 関数内の特定のコンテキストを無効にするための辞書。ここでのキーは、非変異関数のバリアント（存在する場合）です。コンテキストは`ignore_contexts`と同じです。
