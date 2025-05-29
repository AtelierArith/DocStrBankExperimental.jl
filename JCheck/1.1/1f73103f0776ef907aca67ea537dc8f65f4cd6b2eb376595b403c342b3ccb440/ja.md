```
generate([rng=GLOBAL_RNG], T, n)
```

型 `T` の `n` 個のランダムインスタンスをサンプルします。

# 引数

  * `rng::AbstractRNG`: 使用する乱数生成器
  * `T::Type`: インスタンスの型
  * `n::Int`: サンプルする実現の数

# デフォルトジェネレーター

このパッケージには、以下の型に対する `generate` メソッドが含まれています：

  * `AbstractFloat` のサブタイプ
  * `BigInt` を除く `Integer` のサブタイプ
  * `Complex{T <: Real}`
  * `String`
  * `Char`
  * `Array{T, N}`
  * `BitArray{N}`
  * `SquareMatrix{T}`.
  * Julia の LinearAlgebra モジュールによって実装された任意の [特別行列](https://docs.julialang.org/en/v1/stdlib/LinearAlgebra/#Special-matrices)
  * `Union{T...}`
  * `UnitRange{T}`, `StepRange{T, T}`

前のリストでは、`T` は `generate` メソッドが実装されている任意の型を表します。

# 特別行列 (LinearAlgebra)

  * `<...>Triangular{T}` および `<...>Triangular{T, S}` に対してジェネレーターが実装されています。最初のケースでは、`S` は `SquareMatrix{T}` にデフォルト設定されています。`UpperHessenberg` に対しても同じことが言えます。
  * `V` が `Vector{T}` にデフォルト設定される `<...>diagonal{T, V}` に対しても同様の考え方です。
  * 現在、`Symmetric{T, S}` および `Hermitian{T, S}` に対してのみジェネレーターが実装されています。ほとんどの場合、`S` = `SquareMatrix{T}` を指定したいでしょう。

# 配列と文字列

配列と文字列の一般的な目的のジェネレーターは、各サンプル要素の長さを指定する必要があるため、実装が少し難しいです。このパッケージに含まれるデフォルトジェネレーターのために以下の選択がなされました：

  * `String`: 各文字列の長さは平均 64 の指数分布に近いです。
  * `Array{T, N}`: 与えられた配列の各次元の長さは平均 24 ÷ N + 1 の指数分布に近いです（エントリ数を管理可能に保つための低い努力の試みとして）。

これがあなたのニーズに適していない場合は、`generate` を再実装することをためらわないでください。

# 実装

型 `T` のために `generate` を実装する際は、以下の点に留意してください：

  * あなたのメソッドは `Vector{T}` を返すべきです。
  * `generate(T, n)` または `generate([rng, ]Array{T, N}, n) where N` を記述する必要はありません；これは自動的に処理されます。あなたが実装する必要があるのは `generate(::AbstractRNG, ::Type{T}, ::Int)` のみです。
  * `T` に対して [`specialcases`](@ref) および [`shrink`](@ref) を実装することも検討してください。

# 例

```jldoctest
using Random: Xoshiro

rng = Xoshiro(42)

generate(rng, Float32, 10)

# 出力

10-element Vector{Float32}:
 -1.5388016f7
 -5.3113024f-19
 -1.3960648f35
  1.5957566f31
 -4.381218f26
  2.380078f35
  3.878954f9
 -1.1950524f-7
  7.525897f24
 -3.1891005f-12
```
