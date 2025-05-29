ロール構造体を定義するためのマクロ。引数として構造体定義を期待します。

このマクロは3つのことを行います：

1. `ROLE_BASELINE_FIELDS`（ロールコンテキスト）で定義されたすべてのベースラインフィールドを追加します。
2. 指定された構造体にスーパタイプ`Role`を追加します。
3. デフォルト構築のために[`@with_def`](@ref)を適用し、ベースラインフィールドにデフォルト値が割り当てられます。

例えば、使用例は次のようになります。

```julia
@role struct MyRole
	my_own_field::String
end

# 結果は

@with_def mutable struct MyRole <: Role
	# ベースラインフィールド...
	my_own_field::String
    my_own_field_with_default::String = "Default"
end

# したがって、ロールは次のように構築します

my_roel = MyRole("own value", my_own_field_with_default="OtherValue")
```
