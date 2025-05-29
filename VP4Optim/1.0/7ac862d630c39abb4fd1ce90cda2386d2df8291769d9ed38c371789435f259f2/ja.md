```
modpar(T::Type{<: Model}; kwargs...)
```

## 引数

  * `T::Type{<: Model}`: 構築されるモデルの型。
  * `kwargs`: 任意の数のキーワード引数。

## 戻り値

  * 型 `<: ModPar{T}` のインスタンス。

## 備考

  * 最初に [ModPar](@ref ModPar(::Type{<: Model})) を使用してデフォルトパラメータを生成します（これは各モデルに対して実装される必要があります）。
