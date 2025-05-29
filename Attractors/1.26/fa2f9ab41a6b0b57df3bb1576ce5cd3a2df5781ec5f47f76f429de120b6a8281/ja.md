```
convergence_and_basins_fractions(mapper::AttractorMapper, ics)
```

[`basins_fractions`](@ref) の拡張です。`fs, labels, convergence` を返します。最初の2つは `basins_fractions` と同様で、`convergence` は各初期条件がそのアトラクタに収束するのにかかった時間を含むベクトルです。`id = mapper(u0)` をサポートするマッパーでのみ使用可能です。

[`convergence_time`](@ref) も参照してください。

# キーワード引数

  * `show_progress = true`: 進行状況バーを表示します。
