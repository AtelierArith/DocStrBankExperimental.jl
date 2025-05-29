このマクロは構造体定義に適用でき、フィールド宣言時にデフォルト値を定義する可能性を追加します。@kwdefや@with_kwとは対照的に、このマクロはデフォルト値が提供されていない場合、通常のパラメータを構築のために作成します。

# 例

```julia
@with_def struct ExampleStruct
    abc::Int = 0
    def::String
end

# 次のように構築できます
es = ExampleStruct("mydefstring") # abc == 0
es = ExampleStruct("mydefstring", abc=3) # abc == 3
```
