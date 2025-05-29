```
add_position_restraints(sys, k; atom_selector=is_any_atom, restrain_coords=sys.coords)
```

[`System`](@ref) のコピーを返し、原子を拘束するために [`HarmonicPositionRestraint`](@ref) を追加します。

力定数 `k` は単一の値またはシステム内の原子の数と同じ長さの配列であることができます。`atom_selector` 関数は各原子と原子データを受け取り、その原子を拘束するかどうかを判断します。例えば、[`is_heavy_atom`](@ref) は非水素原子が拘束されることを意味します。
