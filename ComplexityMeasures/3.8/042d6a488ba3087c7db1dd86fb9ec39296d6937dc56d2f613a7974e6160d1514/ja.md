```
RelativeFirstDifferenceEncoding <: Encoding
RelativeFirstDifferenceEncoding(minval::Real, maxval::Real; n = 2)
```

`RelativeFirstDifferenceEncoding`は、ベクトルの*最初の差分*の平均が事前に定義された最小値と最大値（それぞれ`minval`と`maxval`）に対して持つ相対的な位置に基づいてベクトルをエンコードします。

## 説明

このエンコーディングは、[Azami2016](@citet)の振幅に配慮した順列エントロピーのアルゴリズムに触発されています。彼らは、状態ベクトルの振幅情報と最初の差分情報の線形結合を使用して確率を修正します。しかし、ここでは、修正の最初の差分部分を整数シンボル`Λ ∈ [1, 2, …, n]`として明示的にエンコードします。エンコーディングの振幅部分は、[`RelativeMeanEncoding`](@ref)エンコーディングとして利用可能です。

## エンコーディング/デコーディング

[`encode`](@ref)と共に使用されると、$m$要素の状態ベクトル$\bf{x} = (x_1, x_2, \ldots, x_m)$は、$Λ = \dfrac{1}{m - 1}\sum_{k=2}^m |x_{k} - x_{k-1}|$としてエンコードされます。$Λ$の値は、任意の単一の$abs(x_k - x_{k-1})$が取ることができる最小/最大値がそれぞれ`minval`/`maxval`であると仮定して、`[0, 1]`の区間に正規化されます。最後に、区間`[0, 1]`は`n`の離散ビンに離散化され、正の整数`1, 2, …, n`で列挙され、正規化された$Λ$が落ちるビンの番号が返されます。状態ベクトルの平均最初の差分が小さいほど、ビン番号は小さくなります。状態ベクトルの平均最初の差分が大きいほど、ビン番号は大きくなります。

[`decode`](@ref)と共に使用されると、正規化された$Λ$が落ちたビンの左端が返されます。

## パフォーマンステクニック

複数の入力ベクトルをエンコードする場合は、[`RelativeFirstDifferenceEncoding`](@ref)インスタンスを構築して再利用する方が効率的です：

```julia
minval, maxval = 0, 1
encoding = RelativeFirstDifferenceEncoding(minval, maxval; n = 4)
pts = [rand(3) for i = 1:1000]
[encode(encoding, x) for x in pts]
```
