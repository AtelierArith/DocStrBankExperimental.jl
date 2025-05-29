```
basins_fractions(basins::AbstractArray [,ids]) → fs::Dict
```

`basins`にエンコードされた引力盆地の状態空間の割合を計算します。`basins`の要素は整数で、`basins`のエントリが収束する引力子を列挙しています（すなわち、[`basins_of_attraction`](@ref)の出力のように）。引力子IDをその相対的な割合にマッピングする辞書を返します。オプションで、選択したIDの割合のみを計算するために`ids`のベクトルを指定できます（デフォルトでは`ids = unique(basins)`）。

[Menck2013](@cite)では、著者はこれらの割合を使用して引力盆地の安定性を定量化し、特にパラメータが変更されたときにどのように変化するかを示しています。これについては、[`global_continuation`](@ref)を参照してください。 ```
