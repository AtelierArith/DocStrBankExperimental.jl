```
rastervalues(sim, raster::Symbol, fieldname::Symbol)
```

指定されたフィールド `fieldnames` の値を持つ、ラスタ `raster` と同じ次元の行列を作成します。ラスタのすべてのセルは同じタイプでなければならず、また `fieldnames` のタイプに対して `zeros` 関数が存在する必要があります。

例:

次のように書く代わりに

```@example
    calc_rasterstate(sim, :raster, c -> c.active, Bool, Cell)
```

単に次のように書くことも可能です。

```@example
    rastervalues(sim, :raster, :active) 
```

[`finish_init!`](@ref) の後にのみ呼び出すことができます。

[`add_raster!`](@ref) および [`calc_rasterstate`](@ref) も参照してください。
