```
abstract type Actor{TCoreState}
```

すべてのアクターのスーパタイプです。

サブタイプは可変でなければならず、作成後に未定義のままにできるフィールド `core::TCoreState` を提供しなければなりません。

# 例

```julia
mutable struct DataHolder{TValue, TCore} <: Actor{TCore}
    value::TValue
    core::TCore
end
```
