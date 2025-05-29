```
y!(mod::Model{Ny,Nx,Nc,T}, new_y::AbstractArray) where {Ny,Nx,Nc,T}
```

新しいデータ値を設定します。

## デフォルト

  * `mod.y::SVector{Ny, T}`を`new_y`の内容でリセットします。
  * `mod.y`の二乗の大きさを計算し、その結果を`mod.y2::Float64`に格納します。
  * 何も返しません。

## 備考

  * ほとんどの場合、[y!](@ref y!)の代わりに[y!](@ref set_data!)を呼び出す方が安全です。
