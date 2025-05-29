```
adjustedrandindex(a::AbstractVector{<:Number}, b::AbstractVector{<:Number}; nbins=50)
```

引数:

  * a, 数値のベクトル
  * b, 数値のベクトル
  * nbins, 連続的な値を離散的に近似するため、離散的な場合はnbins>max*number*of_classesを選択してください
