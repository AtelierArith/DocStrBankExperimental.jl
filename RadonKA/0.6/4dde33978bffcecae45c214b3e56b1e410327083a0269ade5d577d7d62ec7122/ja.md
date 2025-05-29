```
RadonParallelCircle(N, in_height, weights)
```

  * `N` は `radon` の入力配列の最初と二番目の次元のサイズです。
  * `in_height` は、検出器の位置を示すベクトルまたは範囲で、中央値は `N ÷ 2 + 1` にあります。光線は配列を通って直線的な平行経路に沿って移動します。最大値と最小値はそれぞれ `(N+1) ÷ 2 - 1` と `-(N+1) ÷ 2 + 1` です。

例えば、サイズ `N=10` の配列の場合、デフォルトの定義は次のようになります: `RadonParallelCircle(10, -4:4)` したがって、結果のシノグラムの形状は `(9, length(angles), size(array, 3))` になります。

  * `weights` は各光線に異なる強さで重みを付けることができます。デフォルトでは `weights = 0 .* in_height .+ 1` です。

[`radon`](@ref) と [`backproject`](@ref) の使い方を参照してください。
