```
TracyWidom(eigenvalues::AbstractVector{T}; sort_eigenvalues::Bool=true) where T<:Real
```

与えられた固有値のセットに対して、トレーシー・ウィドム統計量とp値を計算します。TODO: 参照を追加。

# 引数

  * `eigenvalues::AbstractVector{T}`: 固有値のベクトル。
  * `sort_eigenvalues::Bool=true`: trueの場合、固有値を降順にソートします。falseの場合、固有値は降順にソートされていると見なされます。

# 戻り値

  * トレーシー・ウィドム統計量とp値を含むタプル。特定の閾値に対して、閾値未満のすべての固有値を保持するのではなく、閾値を超える最初の固有値まで（含まれない）保持することが推奨されます。
