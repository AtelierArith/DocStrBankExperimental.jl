```
wrap_corr!(nav::Array{Float64, 4}, wrapped_points::Array{Int8, 2}, correlation::Union{Array{Float64, 1}, Matrix{Float64}}, slices::Int64)
```

find_wrapped関数で特定されたラップされたポイントをアンラップします。これらの関数は、生理学的記録が利用可能な場合にのみ使用できます。

# 引数

  * `nav::Array{T, 4}` - ナビゲーターデータから得られた位相推定
  * `wrapped_points::Array{Int8, 2}` - ラップされたポイントの位置、find_wrappedの出力
  * `correlation::Union{Array{Float64, 1}` - 各スライスに対するナビゲーター推定と生理学的記録の間の相関値。find_wrappedの出力
  * `slices::Int64` - スライスの数
