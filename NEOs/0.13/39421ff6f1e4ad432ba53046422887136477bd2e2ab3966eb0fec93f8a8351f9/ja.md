```
tsaiod(od::ODProblem{D, T}, params::NEOParameters{T};
    initcond::I = iodinitcond) where {D, I, T <: Real}
```

`od`に対して、変動の多様体上での正規化された平均二乗残差のジェット輸送最小化を通じて予備的な軌道をフィットさせます。

## 引数

  * `od::ODProblem{D, T}`: 軌道決定問題。
  * `params::NEOParameters{T}`: [`NEOParameters`](@ref)の`Too Short Arc Parameters`を参照してください。

## キーワード引数

  * `initcond::I`: 単純な初期条件関数; `AdmissibleRegion{T}`を入力として受け取り、`Vector{Tuple{T, T, Symbol}}`を出力します。各要素は`(ρ, v_ρ, scale)`の形式を持ちます（デフォルト: `iodinitcond`）。
