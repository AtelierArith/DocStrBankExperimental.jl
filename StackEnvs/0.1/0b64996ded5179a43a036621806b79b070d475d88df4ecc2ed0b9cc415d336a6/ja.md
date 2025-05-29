```
struct StackEnv
```

環境スタックで使用される共有環境を定義するためのデータ。

特定のパッケージで作業しているとき、特定のパッケージの依存関係にない他のパッケージを頻繁に使用することがあります。`StackEnv`はこれらの他のパッケージを管理するのに役立ちます。手動でこれを行うこともできますが、何をしたいのか、正確にどうするのかを覚えておくのは時々難しいです。

`StackEnv`は、共有環境を作成し、それが環境スタックにあることを確認するのに役立ち、そのパッケージがアクティブな環境でないときにも見えるようにします。`StackEnv`がアクティブな状態で環境を使って作業することは*意図されていません*。

`StackEnv`を作成し、それを可視化するための最も重要な関数は[`ensure_in_stack`](@ref)です。

# フィールド

  * `name::String`: 追加の環境の名前
  * `packages::Vector{Symbol}`: 環境を初期化するために使用するパッケージのリスト。

[`update_env`](@ref)、[`create_env`](@ref)、[`ensure_in_stack`](@ref)、[`env_exists`](@ref)、[`activate_env`](@ref)、[`is_in_stack`](@ref)、[`delete_from_stack!`](@ref)を参照してください。

# 例

```jldoctest
julia> StackEnv("an_extra_env", [:Example])
StackEnv("an_extra_env", [:Example])

julia> StackEnv("@an_extra_env", [:Example])
StackEnv("an_extra_env", [:Example])
```
