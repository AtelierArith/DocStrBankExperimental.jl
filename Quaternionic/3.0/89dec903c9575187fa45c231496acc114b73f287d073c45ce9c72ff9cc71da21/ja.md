```
distance(q₁, q₂)
distance2(q₁, q₂)
```

2つのクォータニオン間の「距離」を測定するか、`distance2`を使用して二乗距離を測定します。

デフォルトでは、この関数はクォータニオンの*加法*群における自然な測定値を返します：

```julia
abs2(q₁ - q₂)
```

両方の引数が`Rotor`の場合、この関数は*回転*群における自然な測定値を返します。これは大まかに言うと、

```julia
abs2(log(q₁ / q₂))
```

であることに注意してください。`Rotor`の場合、このメソッドは`q₁`と`q₂`のスケーリングに（効率的に）依存せず、-1の因子まで含まれ、回転群に適切です。

# 例

```jldoctest example
julia> distance(imx, imy)
1.4142135623730951
julia> distance(rotor(imx), rotor(imy))
1.5707963267948966
julia> distance(imz, -imz)
2.0
julia> distance(rotor(imz), rotor(-imz))
0.0
```
