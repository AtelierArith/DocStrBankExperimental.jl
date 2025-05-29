```
air_density(Tₐ, P; check=true)
air_density(Tₐ, P, Rd, K₀; check=true)
```

ρ, 空気密度 (kg m-3)。

# 引数

  * `Tₐ` (摂氏度): 空気温度
  * `P` (kPa): 空気圧
  * `Rd` (J kg-1 K-1): 乾燥空気の気体定数 (Foken p. 245、または R bigleaf パッケージを参照)。
  * `K₀` (摂氏度): 0 ケルビンでの摂氏度
  * `check` (Bool): P が 85-110 kPa の地球範囲内にあるかどうかを確認

# 注意

Rd と K₀ は、提供されていない場合は [`Constants`](@ref) から取得されます。

# 参考文献

Foken, T, 2008: Micrometeorology. Springer, Berlin, Germany.
