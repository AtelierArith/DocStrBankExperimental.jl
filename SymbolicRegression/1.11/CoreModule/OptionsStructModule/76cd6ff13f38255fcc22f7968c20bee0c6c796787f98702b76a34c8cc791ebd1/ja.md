```
AbstractOptions
```

SymbolicRegression.jlのすべての検索ハイパーパラメータを格納する抽象型です。標準の実装は[`Options`](@ref)です。

特定の関数をオーバーライドしたり、新しい動作を作成するために、`AbstractOptions`の新しいサブタイプを作成したい場合があります。この新しい型が[`Options`](@ref)のすべてのプロパティを持っていることを確認してください。

たとえば、`Options`に追加したい新しいオプションがある場合：

```julia
Base.@kwdef struct MyNewOptions
    a::Float64 = 1.0
    b::Int = 3
end
```

各対応する型にプロパティを転送する結合オプション型を作成できます：

```julia
struct MyOptions{O<:SymbolicRegression.Options} <: SymbolicRegression.AbstractOptions
    new_options::MyNewOptions
    sr_options::O
end
const NEW_OPTIONS_KEYS = fieldnames(MyNewOptions)

# 両方のパラメータセットを持つコンストラクタ：
function MyOptions(; kws...)
    new_options_keys = filter(k -> k in NEW_OPTIONS_KEYS, keys(kws))
    new_options = MyNewOptions(; NamedTuple(new_options_keys .=> Tuple(kws[k] for k in new_options_keys))...)
    sr_options_keys = filter(k -> !(k in NEW_OPTIONS_KEYS), keys(kws))
    sr_options = SymbolicRegression.Options(; NamedTuple(sr_options_keys .=> Tuple(kws[k] for k in sr_options_keys))...)
    return MyOptions(new_options, sr_options)
end

# すべての`Options`を利用可能にしつつ、`new_options`にもアクセス可能にする
function Base.getproperty(options::MyOptions, k::Symbol)
    if k in NEW_OPTIONS_KEYS
        return getproperty(getfield(options, :new_options), k)
    else
        return getproperty(getfield(options, :sr_options), k)
    end
end

Base.propertynames(options::MyOptions) = (NEW_OPTIONS_KEYS..., fieldnames(SymbolicRegression.Options)...)
```

これにより、`MyOptions`オブジェクトから`a`と`b`にアクセスできるようになり、SymbolicRegression.jlの内部メソッドで`Options`のすべてのプロパティを利用可能にします。
