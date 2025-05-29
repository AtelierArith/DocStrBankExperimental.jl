```
Optimisers.apply!(rule::RuleType, state, parameters, gradient) -> (state, gradient)
```

これは任意の最適化ルールの動作を定義します。これは、パラメータから減算される修正された勾配と、次の反復で使用するための更新された状態（ある場合）をタプル `(state, gradient)` として返す必要があります。

効率のために、古い状態を変更することは自由ですが、返されるものだけが使用されます。理想的には、これは `maywrite(x)` をチェックするべきであり、組み込みルールは [`@..`](@ref) を介してそれを行います。

初期状態は `init(rule::RuleType, parameters)` です。

# 例

```jldoctest
julia> Optimisers.init(Descent(0.1), Float32[1,2,3]) === nothing
true

julia> Optimisers.apply!(Descent(0.1), nothing, Float32[1,2,3], [4,5,6])
(nothing, Base.Broadcast.Broadcasted{Base.Broadcast.DefaultArrayStyle{1}}(*, ([4, 5, 6], 0.1f0)))
```
