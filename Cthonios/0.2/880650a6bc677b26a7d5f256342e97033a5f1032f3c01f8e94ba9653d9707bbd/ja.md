```julia
struct Section{P, M} <: Cthonios.AbstractSectionInput
```

  * `block_name::String`
  * `q_order::Int64`
  * `physics::Any`
  * `props::Any`

セクション入力。 `physics` - このセクションで使用する物理オブジェクト。 `block_name` - セクションを構築するためのエクソダスブロックの名前。 `q_order` - 使用する数値積分の次数。
