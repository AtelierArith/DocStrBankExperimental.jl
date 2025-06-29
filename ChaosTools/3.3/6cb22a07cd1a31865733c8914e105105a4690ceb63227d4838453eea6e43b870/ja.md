```
orbitdiagram(ds::DynamicalSystem, i, p_index, pvalues; kwargs...) → od
```

与えられた力学系の軌道図（時には誤って分岐図と呼ばれる）を計算し、パラメータ値 `pvalues` のために `i` 変数を保存します。 `p_index` は、`set_parameter!(ds, p_index, pvalue)` を介して変更するパラメータを指定します。これは、`DeterministicIteratedMap`、`StroboscopicMap`、`PoincareMap` のいずれかである場合に最も意味がありますが、あらゆる種類の `DynamicalSystem` に対して機能します。

軌道図は、`ds` が進化するにつれての `ds` の最後の `n` 状態のコレクションに過ぎません。これは、各パラメータ値について行われます。

`i` は `Int` または `AbstractVector{Int}` であることができます。`i` が `Int` の場合、`od` はベクトルのベクトルです。そうでない場合、`od` はベクトルのベクトルのベクトルです。各エントリ `od` の `od` は、各パラメータ値での点であり、`length(od) == length(pvalues)` かつ `length(od[j]) == n, ∀ j` です。

## キーワード引数

  * `n::Int = 100`: 各パラメータ値のために保存する点の数。
  * `Δt = 1`: 点を保存する間のステッピング時間。
  * `u0 = nothing`: 初期状態を指定します。`nothing` の場合、各パラメータの後の前の状態が新しいパラメータでの新しい初期条件のシードとして使用されます（最初の状態はシステムの状態です）。これにより、アトラクタへの収束が速くなり、より小さな `Ttr` が必要になります。そうでない場合、`u0` は標準状態または状態のベクトルであり、各パラメータに対して特定の状態が使用されます。
  * `Ttr::Int = 10`: 各軌道は出力を保存する前に最初に `Ttr` だけ進化します。
  * `ulims = (-Inf, Inf)`: `ulims` 内のシステム状態のみを記録します（`i` が `Int` の場合のみ有効）。`n` 状態が `ulims` 内に入るまで反復が続きます。
  * `show_progress = false`: 進行状況バーを表示します（パラメータ値をカウントします）。
  * `periods = nothing`: `ds` が `StroboscopicMap` の場合のみ有効です。指定された場合、`pvalues` と同じレイアウトのコンテナでなければなりません。各パラメータ値のための `period` の値を提供します。軌道図が駆動周波数に対して生成される場合に便利です。
