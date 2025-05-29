```
rulemetrics(
    r::Rule,
    X::AbstractInterpretationSet,
    Y::AbstractVector{<:Label}
)
```

ラベル付きデータセットに関してルールのメトリクスを計算し、次の要素からなる `NamedTuple` を返します：

  * `support`: ルールの前件を満たすインスタンスの数を総インスタンス数で割ったもの；
  * `error`:

      * 分類問題の場合: 正しく分類されなかったインスタンスの数を総インスタンス数で割ったもの；
      * 回帰問題の場合: 平均二乗誤差；
  * `length`: ルールの前件に含まれる原子の数。

他にも [`Rule`](@ref), [`SoleLogics.AbstractInterpretationSet`](@ref), [`Label`](@ref), [`evaluaterule`](@ref), [`outcometype`](@ref), [`consequent`](@ref) を参照してください。
