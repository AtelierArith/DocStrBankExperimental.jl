```
orbitdetermination(od::ODProblem{D, T}, params::NEOParameters{T};
    kwargs...) where {D, I, T <: Real}
```

初期軌道決定 (IOD) ルーチン。

## 引数

  * `od::ODProblem{D, T}`: 軌道決定問題。
  * `params::NEOParameters{T}`: [`NEOParameters`](@ref) を参照。

## キーワード引数

  * `initcond::I`: 単純な初期条件関数; `AdmissibleRegion{T}` を入力として受け取り、`Vector{Tuple{T, T, Symbol}}` を出力します。各要素は `(ρ, v_ρ, scale)` の形式を持ちます (デフォルト: `iodinitcond`)。

!!! 警告     この関数は (グローバルな) `TaylorSeries` 変数を変更します。
