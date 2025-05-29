```julia
ismassaction(rx, rs; rxvars = get_variables(rx.rate),
                              haveivdep = nothing,
                              unknownset = Set(unknowns(rs)),
                              ivset = nothing)
```

与えられた反応が質量作用形式である場合は真です。すなわち、`rx.rate`はシステムの未知数に対応する化学種に依存せず、独立変数（通常は時間）に明示的に依存しません。

# 引数

  * `rx`、[`Reaction`](@ref)。
  * `rs`、反応を含む[`ReactionSystem`](@ref)。
  * オプション: `rxvars`、`rxvars`に含まれない`Variable`は可能な依存関係として無視されます。
  * オプション: `haveivdep`、[`Reaction`](@ref)の`rate`フィールドが任意の独立変数（すなわちtまたは空間システムの場合はx,yなど）に明示的に依存する場合は真です。設定されていない場合は、自動的に計算されます。
  * オプション: `unknownset`、`rxvars`が含まれている場合、`rx`は非質量作用である未知数の集合。
  * オプション: `ivset`、システムの独立変数の`Set`。提供されていない場合、システムが空間的である場合（すなわち`isspatial(rs) == true`）、すべての空間変数と時間変数を含むように作成されます。レート式が`ivset`の任意の要素を含む場合、`ismassaction(rx,rs) == false`になります。この動作を制御するためにカスタムセットを渡してください。

注意:

  * 非整数の化学量論は非質量作用として扱われます。これには、化学量論係数のための記号変数/項または浮動小数点数が含まれます。
