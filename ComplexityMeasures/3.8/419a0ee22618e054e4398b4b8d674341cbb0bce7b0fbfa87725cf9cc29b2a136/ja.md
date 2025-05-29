```
CombinationEncoding <: Encoding
CombinationEncoding(encodings)
```

`CombinationEncoding`は複数の[`Encoding`](@ref)を受け取り、与えられた`encodings`に互換性のある入力をエンコードするために使用できる結合エンコーディングを作成します。

## エンコーディング/デコーディング

[`encode`](@ref)と共に使用されると、`encodings`内の各[`Encoding`](@ref)は、特定のエンコーディングの結果の総数である`n_e`に対して、整数のセット`1, 2, …, n_e`を返します。`k`個の異なるエンコーディングを使用することで、直交座標`(c₁, c₂, …, cₖ)`（`cᵢ ∈ 1, 2, …, n_i`）を構築でき、これは整数によって一意に識別されます。したがって、各ユニークな*結合*エンコーディングを単一の整数で識別できます。

[`decode`](@ref)と共に使用されると、整数シンボルは対応する直交座標に変換され、各エンコーディングのデコードされたシンボルを取得するために使用され、デコードされたシンボルのタプルが返されます。

結果の総数は`prod(total_outcomes(e) for e in encodings)`です。

## 例

```julia
using ComplexityMeasures

# ベクトル`x`をエンコードしたい。
x = [0.9, 0.2, 0.3]

# そのために、初差分エンコーディング、振幅エンコーディング、
# および順序パターンエンコーディングの組み合わせを使用します。

encodings = (
    RelativeFirstDifferenceEncoding(0, 1; n = 2),
    RelativeMeanEncoding(0, 1; n = 5),
    OrdinalPatternEncoding(3) # xは三要素のベクトルです
    )
c = CombinationEncoding(encodings)

# `x`を整数としてエンコード
ω = encode(c, x)

# シンボルをデコード（各エンコーディング`e ∈ encodings`のデコーディングのベクトルに）。
# この特定のケースでは、最初の2つの要素は左ビンのエッジになり、
# 最後の要素はデコードされた順序パターン（`x`をソートするインデックス）になります。
d = decode(c, ω)
```
