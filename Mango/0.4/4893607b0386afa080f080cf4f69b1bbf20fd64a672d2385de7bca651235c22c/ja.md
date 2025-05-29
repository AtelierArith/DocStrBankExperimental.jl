エージェント構造体を定義するためのマクロ。引数として構造体定義を期待します。

このマクロは3つのことを行います：

1. `AGENT_BASELINE_FIELDS`で定義されたすべてのベースラインフィールド（エージェントコンテキスト`context`、ロールハンドラ`role_handler`、および`aid`）を追加します。
2. 指定された構造体にスーパタイプ`Agent`を追加します。
3. デフォルト構築のために[`@with_def`](@ref)を適用し、ベースラインフィールドにデフォルト値が割り当てられます。

# 例

例えば、使用例は次のようになります。

```julia
@agent struct MyAgent
	my_own_field::String
end

# 結果は

@with_def mutable struct MyAgent <: Agent
	# ベースラインフィールド...
	my_own_field::String
    my_own_field_with_default::String = "Default"
end

# したがって、エージェントは次のように構築します

my_agent = MyAgent("own value", my_own_field_with_default="OtherValue")
```
