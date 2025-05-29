```
次元
```

物理量の次元。

次元は、SIシステムの7つの基本次元それぞれの累乗を表すコレクション $(a, b, c, d, e, f, g)$ として表現されます。

$$
\mathrm{M}^a \, \mathrm{L}^b \, \mathrm{T}^c \, \mathrm{I}^d \, \mathrm{\Theta}^e \, \mathrm{N}^f \, \mathrm{J}^g,
$$

ここで

  * $$
    \mathrm{M}
    $$

    : 質量次元
  * $$
    \mathrm{L}
    $$

    : 長さ次元
  * $$
    \mathrm{T}
    $$

    : 時間次元
  * $$
    \mathrm{I}
    $$

    : 電流次元
  * $$
    \mathrm{\Theta}
    $$

    : 温度次元
  * $$
    \mathrm{N}
    $$

    : 物質量次元
  * $$
    \mathrm{J}
    $$

    : 光度次元

# フィールド

  * `massExponent::Real`: 質量次元の指数 $a$
  * `lengthExponent::Real`: 長さ次元の指数 $b$
  * `timeExponent::Real`: 時間次元の指数 $c$
  * `currentExponent::Real`: 電流次元の指数 $d$
  * `temperatureExponent::Real`: 温度次元の指数 $e$
  * `amountExponent::Real`: 物質量次元の指数 $f$
  * `luminousIntensityExponent::Real`: 光度次元の指数 $g$

# コンストラクタ

```
Dimension(; M::Real=0, L::Real=0, T::Real=0, I::Real=0, θ::Real=0, N::Real=0, J::Real=0)
```

# 例外を発生させる

  * `Core.DomainError`: 無限大の数で任意のフィールドを初期化しようとした場合

# 備考

コンストラクタは、可能であれば任意の指数を `Int` に変換します。

# 例

エネルギーを表す量は次元

$$
 \mathrm{M} \, \mathrm{L}^{2} \, \mathrm{T}^{-2}
$$

に属します。

対応する `Dimension` オブジェクトは次のとおりです：

```jldoctest
julia> Dimension(M=1, L=2, T=-2)
Dimension M^1 L^2 T^-2
```

キーワード引数なしでコンストラクタを呼び出すと、次元のない量に対応する指数が返されます：

```jldoctest
julia> Dimension()
Dimension 1
```
