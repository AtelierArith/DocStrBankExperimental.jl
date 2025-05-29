```
ValidationLieGroup{L<:AbstractLieGroup} <: AbstractLieGroup
```

入力パラメータと[`LieGroups`](@ref)に対して定義された関数の出力値をテストするためのLie群です。

`ignore_contexts`キーワードを使用すると、無視するコンテキストの単一の`Symbol`または`Symbols`のベクトルを指定できます。

現在のコンテキストは次のとおりです。

  * `:All`: すべてのチェックを無効にします
  * `:Point`: 点に関するチェック
  * `:Algebra`: [`LieAlgebra`](@ref)に関連するチェック
  * `:Output`: 出力に関するチェック
  * `:Input`: 入力変数に関するチェック

# フィールド

  * `lie_group::L` 装飾される[`AbstractLieGroup`](@ref)
  * `mode::Symbol`: エラーハンドリングに使用されるモード、`:error`または`:warn`
  * `ignore_contexts::AbstractVector{Symbol}`: 検証で無視されるコンテキストを格納します。
  * `ignore_functions::Dict{<:Function,<:Union{Symbol,<:AbstractVector{Symbol}}`: 関数またはその変異バリアント内で無視されるコンテキストを格納します。

最初のフィールドを除いて、他のすべてのフィールドは[`ValidationManifold`](@extref `ManifoldsBase.ValidationManifold`)のセットアップに類似しています。それらの意味に関する詳細な例については、これらのドキュメントを参照してください。

# コンストラクタ

```
ValidationLieGroup(L::AbstractLieGroup, check_manifold=true; kwargs...)
```

指定された[`AbstractLieGroup`](@ref) `L`のためのValidation Lie Groupを生成します。`check_manifold`が`true`に設定されている場合、内部マニホールドは追加で[`ValidationManifold`](@extref `ManifoldsBase.ValidationManifold`)でラップされます。すべての適切なキーワードは、検証マニホールドのコンストラクタにも渡されます。

# キーワード引数

  * `error::Symbol=:error`: 検証中のエラーがどのように報告されるべきかを指定します。これは[`is_point`](@extref `ManifoldsBase.is_point`)および[`is_vector`](@extref `ManifoldsBase.is_vector`)に`error`キーワード引数として渡されます。利用可能な値は`:error`、`:warn`、`:info`、および`:none`です。他のすべての値は`:none`として扱われます。
  * `ignore_contexts = Vector{Symbol}()` 検証が実行されるべきでないコンテキストを示すベクトル。
  * `ignore_functions=Dict{Function,Union{Symbol,Vector{Symbol}}}()` 関数内で特定のコンテキストを無効にするための辞書。ここでのキーは非変異関数のバリアント（存在する場合）です。コンテキストは`ignore_contexts`と同じです。
