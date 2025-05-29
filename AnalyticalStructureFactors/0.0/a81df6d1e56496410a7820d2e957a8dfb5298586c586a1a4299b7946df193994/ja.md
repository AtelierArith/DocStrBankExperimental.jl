```
blip(temperature::T_num; ν::Integer = 6) where {T_num<:AbstractFloat}
```

ソフトポテンシャルの「blip」関数形式に基づいて、効果的なハードスフィア直径 (λ) を計算します。この関数は、λ と λ³ の両方を返します。

λ³ の公式は次のとおりです: λ³(T, ν) = 1 - 3 * ∫_0^1 dx x² * exp(-(1/T) * ((1/x^ν) - 1)²)

# 引数

  * `temperature::T_num`: 系の無次元温度。

# キーワード

  * `ν::Integer = 6`: ポテンシャルの反発部分の「柔らかさ」または急峻さを調整するパラメータ。

# 戻り値

  * `Tuple{T_num, T_num}`: `(λ, λ³)` を含むタプルで、ここで `λ` は効果的な直径、`λ³` はその立方体です。

# 参考文献

[1] Luis Enrique Sánchez-Díaz, Pedro Ramírez-González, and Magdaleno Medina-Noyola.     Phys. Rev. E 87, 052306 – Published 22 May 2013.
