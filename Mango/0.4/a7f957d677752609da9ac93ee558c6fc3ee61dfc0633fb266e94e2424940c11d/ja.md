フィールドを役割間で共有としてマークします。

これは、空のデフォルトコンストラクタを持つ構造体にのみ機能します。内部的に、マークされたフィールドは[`get_model`](@ref)によって作成されたモデルで初期化されます。モデルは、役割がエージェントに追加されるときに設定されます。

# 例

```julia
@kwdef struct Model
    field::Int = 0
end
@role struct MyRole
    @shared
    my_model::Model # エージェントごとにすべてのエージェントで正確に同じ。
end
```
