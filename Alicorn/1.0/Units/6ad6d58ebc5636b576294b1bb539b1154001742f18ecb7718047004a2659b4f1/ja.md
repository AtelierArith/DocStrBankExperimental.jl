```
BaseUnitExponents
```

七つのSI基本単位それぞれの累乗を表す指数のコレクション。

指数 $(a, b, c, d, e, f, g)$ は、七つのSI基本単位が累乗されるべきパワーとして解釈されます：

$$
\mathrm{kg}^a \, \mathrm{m}^b \, \mathrm{s}^c \, \mathrm{A}^d \, \mathrm{K}^e \, \mathrm{mol}^f \, \mathrm{cd}^g.
$$

[`BaseUnit`](@ref) 型は、`BaseUnitExponents` を使用して基本単位に基づいて名前付き単位を定義します。

# フィールド

  * `kilogramExponent::Real`: キログラムのパワー $a$
  * `meterExponent::Real`: メートルのパワー $b$
  * `secondExponent::Real`: 秒のパワー $c$
  * `ampereExponent::Real`: アンペアのパワー $d$
  * `kelvinExponent::Real`: ケルビンのパワー $e$
  * `molExponent::Real`: モルのパワー $f$
  * `candelaExponent::Real`: カンデラのパワー $g$

# コンストラクタ

```
BaseUnitExponents(; kg::Real=0, m::Real=0, s::Real=0, A::Real=0, K::Real=0, mol::Real=0, cd::Real=0)
```

# 例外を発生させる条件

  * `Core.DomainError`: 無限の数で任意のフィールドを初期化しようとした場合

# 備考

コンストラクタは、可能であれば任意の指数を `Int` に変換します。

# 例

ジュールは次のように定義されます。

$$
 1\,\mathrm{J} = 1\,\mathrm{kg}\,\mathrm{m^2}\,\mathrm{s^{-2}}.
$$

対応する `BaseUnitExponents` オブジェクトは次の通りです：

```jldoctest
julia> BaseUnitExponents(kg=1, m=2, s=-2)
BaseUnitExponents kg^1 m^2 s^-2 A^0 K^0 mol^0 cd^0
```

キーワード引数なしでコンストラクタを呼び出すと、次元のない単位に対応する指数が返されます：

```jldoctest
julia> BaseUnitExponents()
BaseUnitExponents kg^0 m^0 s^0 A^0 K^0 mol^0 cd^0
```
