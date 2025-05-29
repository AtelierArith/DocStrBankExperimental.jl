```
groebner_learn(polynomials; options...)
```

`polynomials`によって生成されたイデアルのグレブナー基底を計算し、トレースを出力します。

トレースは、`groebner_learn`が適用されたのと同じイデアルの特化のグレブナー基底の計算を高速化するために使用できます。

`groebner_apply!`も参照してください。

## 引数

  * `polynomials`: 多項式の配列。`GF(p)`または`Native.GF(p)`上のAbstractAlgebra.jlまたはNemo.jlの多項式でなければなりません。

## 戻り値

タプル（`trace`、`basis`）を返します。

  * `trace`: オブジェクト、トレース。`groebner_apply!`で使用できます。
  * `basis`: 多項式の配列、グレブナー基底。

## 可能なオプション

`groebner`と同じです。

## 例

同じ基底体上で`groebner_learn`と`groebner_apply!`を使用する：

```@example
using Groebner, AbstractAlgebra
R, (x, y) = GF(2^31-1)["x", "y"]

# 学習
trace, gb_1 = groebner_learn([x*y^2 + x, y*x^2 + y])

# 適用（同じサポート、異なる係数）
flag, gb_2 = groebner_apply!(trace, [2x*y^2 + 3x, 4y*x^2 + 5y])

@assert flag
```

異なる基底体上で`groebner_learn`と`groebner_apply!`を使用する：

```@example
using Groebner, AbstractAlgebra
R, (x, y) = GF(2^31-1)["x", "y"]

# 学習
trace, gb_1 = groebner_learn([x*y^2 + x, y*x^2 + y], ordering=DegRevLex())

# 異なる剰余でリングを作成
R2, (x2, y2) = GF(2^30+3)["x", "y"]

# 適用（異なる剰余）
flag, gb_2 = groebner_apply!(
    trace, 
    [2x2*y2^2 + 3x2, 4y2*x2^2 + 5y2], 
    ordering=DegRevLex()
)

@assert flag
@assert gb_2 == groebner([2x2*y2^2 + 3x2, 4y2*x2^2 + 5y2], ordering=DegRevLex())
```

バッチで`groebner_apply!`を使用する：

```@example
using Groebner, AbstractAlgebra
R, (x, y) = polynomial_ring(GF(2^31-1), ["x", "y"], internal_ordering=:degrevlex)

# 学習
trace, gb_1 = groebner_learn([x*y^2 + x, y*x^2 + y])

# 他の剰余を持つリングを作成
R2, (x2, y2) = polynomial_ring(GF(2^30+3), ["x", "y"], internal_ordering=:degrevlex)
R3, (x3, y3) = polynomial_ring(GF(2^27+29), ["x", "y"], internal_ordering=:degrevlex)

# 同じイデアルの2つの特化
batch = ([2x2*y2^2 + 3x2, 4y2*x2^2 + 5y2], [4x3*y3^2 + 4x3, 5y3*x3^2 + 7y3])

# 一度に2つの多項式のセットに適用
flag, (gb_2, gb_3) = groebner_apply!(trace, batch)

@assert flag
@assert (gb_2, gb_3) == map(groebner, batch)
```

おそらく、より複雑な例では、Katsura-9システムのグレブナー基底を計算します：

```@example
using Groebner, AbstractAlgebra, BenchmarkTools

# システムを作成
kat = Groebner.Examples.katsuran(9, k=ZZ, internal_ordering=:degrevlex)

# 5つの異なる素数で係数を剰余
kat_0 = map(f -> map_coefficients(c -> GF(2^30 + 3)(c), f), kat)
kat_1 = map(f -> map_coefficients(c -> GF(2^30 + 7)(c), f), kat)
kat_2 = map(f -> map_coefficients(c -> GF(2^30 + 9)(c), f), kat)
kat_3 = map(f -> map_coefficients(c -> GF(2^30 + 15)(c), f), kat)
kat_4 = map(f -> map_coefficients(c -> GF(2^30 + 19)(c), f), kat)

# トレースを学習
trace, gb_0 = groebner_learn(kat_0);

# 1つの入力と4つの異なる入力での適用のパフォーマンスを比較：

# 1つのシステムに適用
@btime groebner_apply!($trace, $kat_1);
#  46.824 ms (19260 allocations: 24.48 MiB)

# 4つのシステムのバッチに適用
@btime groebner_apply!($trace, $(kat_1, kat_2, kat_3, kat_4));
#  72.813 ms (23722 allocations: 59.44 MiB)
```

合成された`groebner_apply!`の方がより良い償却パフォーマンスを示すことに注意してください。

## 注意事項

  * この関数はスレッドセーフです。

```
