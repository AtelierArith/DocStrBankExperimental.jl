```
extract_final_state(smld::SMLD)
```

シミュレーションの最終フレームからエミッターを抽出し、開始条件として使用します。

# 引数

  * `smld::SMLD`: シミュレーションからのエミッターを含むSMLD

# 戻り値

  * `Vector{<:AbstractEmitter}`: 最終フレームからのエミッター

# 例

```julia
# シミュレーションを実行
params = DiffusionSMLMParams(t_max=5.0)
smld = simulate(params)

# 最終状態を抽出
final_state = extract_final_state(smld)

# 新しいパラメータでシミュレーションを続行
params_new = DiffusionSMLMParams(t_max=10.0, diff_monomer=0.2)
smld_continued = simulate(params_new; starting_conditions=final_state)
```
