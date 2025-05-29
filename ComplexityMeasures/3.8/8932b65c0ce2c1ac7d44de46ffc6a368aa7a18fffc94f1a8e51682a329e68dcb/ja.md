```
GaussianCDFEncoding <: Encoding
GaussianCDFEncoding{m}(; μ, σ, c::Int = 3)
```

スカラーまたはベクトル `χ` を正規累積分布関数 (NCDF) に基づいて整数 `sᵢ ∈ [1, 2, …, c]` のいずれかに [`encode`](@ref) するエンコーディングスキームであり、[`decode`](@ref) では `sᵢ` を `[0, 1]` の部分区間に変換します（情報の一部が失われます）。

## `GaussianCDFEncoding` の初期化

エンコードされる入力のサイズは事前に知られている必要があります。したがって、`m = length(χ)` を設定する必要があります。ここで `χ` は入力であり（スカラーの場合は `m = 1`、ベクトルの場合は `m ≥ 2`）、`m` を型パラメータとして明示的に指定する必要があります。例えば、3要素のベクトルをエンコードするには `encoding = GaussianCDFEncoding{3}(; μ = 0.0, σ = 0.1)` とし、スカラーをエンコードするには `encoding = GaussianCDFEncoding{1}(; μ = 0.0, σ = 0.1)` とします。

## 説明

### スカラーのエンコーディング/デコーディング

`GaussianCDFEncoding` は、入力スカラー $χ$ を与えられた平均 `μ` と標準偏差 `σ` を用いて正規累積分布関数 (CDF) によって新しい実数 $y_ \in [0, 1]$ にマッピングします。これは次のマップに従います。

$$
x \to y : y = \dfrac{1}{ \sigma
    \sqrt{2 \pi}} \int_{-\infty}^{x} e^{(-(x - \mu)^2)/(2 \sigma^2)} dx.
$$

次に、区間 `[0, 1]` は等間隔にビン分けされ、$1, 2, \ldots, c$ と列挙され、$y$ は線形マップ $y \to z : z = \text{floor}(y(c-1)) + 1$ を使用してこれらの整数のいずれかに線形にマッピングされます。

フロア操作のため、いくつかの情報が失われるため、[`decode`](@ref) と共に使用されると、各デコードされた `sᵢ` は `[0, 1]` の *部分区間* にマッピングされます。この部分区間は長さ `1` の `Vector{SVector}` として返されます。

デコーディングステップは、`GaussianCDFEncoding` を内部で使用する推定器のいかなる結果空間の要素も生成しないことに注意してください。これは、これらの推定器がエンコードされたデータを追加で遅延埋め込むためです。

### ベクトルのエンコーディング/デコーディング

`GaussianCDFEncoding` がベクトル `χ` と共に使用される場合、`χ` の各要素は別々にエンコードされ、整数の `length(χ)` シーケンスが生成され、これは `CartesianIndex` として扱うことができます。エンコードされたシンボル `s ∈ [1, 2, …, c]` は、このカーテシアンインデックスに対応する線形インデックスに過ぎません（[`CombinationEncoding`](@ref) の動作に似ています）。

[`decode`](@ref) されると、整数シンボル `s` はその `CartesianIndex` 表現に戻され、これは `[0, 1]` 区間の細分を参照する整数のシーケンスに過ぎません。関連する部分区間は、長さ `χ` の `Vector{SVector}` として返されます。

## 例

```jldoctest
julia> using ComplexityMeasures, Statistics

julia> x = [0.1, 0.4, 0.7, -2.1, 8.0];

julia> μ, σ = mean(x), std(x); encoding = GaussianCDFEncoding(; μ, σ, c = 5)

julia> es = encode.(Ref(encoding), x)
5-element Vector{Int64}:
 2
 2
 3
 1
 5

julia> decode(encoding, 3)
2-element SVector{2, Float64} with indices SOneTo(2):
 0.4
 0.6
```
