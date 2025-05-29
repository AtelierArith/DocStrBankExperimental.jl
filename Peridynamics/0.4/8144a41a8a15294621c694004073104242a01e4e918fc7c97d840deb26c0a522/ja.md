```
precrack!(body, set_a, set_b; update_dmg=true)
```

2つの点のセット間に亀裂を作成し、異なる点のセットのポイント間の相互作用を禁止します。 `set_a`のポイントは`set_b`のポイントと相互作用することはできません。

# 引数

  * `body::AbstractBody`: [`Body`](@ref)。
  * `set_a::Symbol`: このボディの点のセットの名前。
  * `set_b::Symbol`: このボディの点のセットの名前。

# キーワード

  * `update_dmg::Bool`: `true`の場合、事前定義された亀裂に関与する材料ポイントは初期的に損傷を受けます。 `false`の場合、関与する結合は削除され、事前定義された亀裂に関与する材料ポイントは参照結果で損傷を受けません。 （デフォルト: `true`）

# 例外

  * ボディが`set_a`および`set_b`という名前のセットを含まない場合、エラーが発生します。
  * 点のセットが交差し、ポイントが両方のセットに含まれている場合、エラーが発生します。

# 例

```julia-repl
julia> point_set!(body, :a, 1:2)

julia> point_set!(body, :b, 3:4)

julia> precrack!(body, :a, :b)

julia> body
1000-point Body{BBMaterial{NoCorrection}}:
  3 point set(s):
    1000-point set `all_points`
    2-point set `a`
    2-point set `b`
  1 predefined crack(s)
```
