```
struct UnivariateFeature{U,I<:VariableId} <: AbstractUnivariateFeature
    i_variable::I
    f::Function
    fname::Union{Nothing,String}
end
```

次元チャネルの単一変数に対して一般的な関数 `f` を適用することによって表される次元的特徴。例えば、画像上で解釈されたときに `Interval2D` の世界がどれだけ赤を含んでいるかを計算するスカラー関数をラップすることができます。オプションとして、関数に特徴名 `fname` を付けることができ、これは検査に役立ちます（例えば、`f` が匿名関数である場合、"#47" や "#49" のような名前を避けることができます）。

さらに [`SoleLogics.Interval`](@ref), [`SoleLogics.Interval2D`](@ref), [`AbstractUnivariateFeature`](@ref), [`VarFeature`](@ref), [`AbstractFeature`](@ref) を参照してください。
