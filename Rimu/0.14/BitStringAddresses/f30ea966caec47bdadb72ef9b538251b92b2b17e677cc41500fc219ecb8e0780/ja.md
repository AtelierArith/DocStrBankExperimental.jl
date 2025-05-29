```
SingleComponentFockAddress{N,M} <: AbstractFockAddress{N,M}
```

`N` 粒子と `M` モードを持つ単一成分フォック状態を表す型です。

実装されたサブタイプ: [`BoseFS`](@ref), [`FermiFS`](@ref)。

# サポートされている機能

  * [`find_mode`](@ref)
  * [`find_occupied_mode`](@ref)
  * [`num_occupied_modes`](@ref)
  * [`occupied_modes`](@ref): 遅延イテレータ。
  * [`OccupiedModeMap`](@ref): 即時構築を持つ `AbstractVector`。
  * [`excitation`](@ref): 新しいアドレスを作成します。
  * インデックス付けのための [`BoseFSIndex`](@ref) と [`FermiFSIndex`](@ref)。

さらに [`CompositeFS`](@ref), [`AbstractFockAddress`](@ref) も参照してください。
