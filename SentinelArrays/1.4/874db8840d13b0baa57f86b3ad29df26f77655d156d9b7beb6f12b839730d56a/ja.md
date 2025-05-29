```
SentinelArray(A::AbstractArray, sentinel, value)
SentinelVector{T}(undef, len, sentinel, value)
SentinelMatrix{T}(undef, dims, sentinel, value)
SentinelArray{T, N}(undef, dims, sentinel, value)
```

既存の `AbstractArray` をラップするか、標準の `undef` パターンを使用して `SentinelArray` を構築します。このパターンでは、最初に `Array` を構築し、それを `SentinelArray` でラップします。

`SentinelArray{T}` は型 `T` の `AbstractArray` をラップし、`sentinel` と `value` 引数を受け入れます。ラップされた配列に `sentinel` と等しい要素がある場合、代わりに `value` が返されます。これにより、例えば `SentinelVector{Float64}(undef, len, NaN, missing)` のようにして `Vector{Union{Float64, Missing}}` をシミュレートすることができます。結果として得られる `SentinelArray` の `eltype` は `Union{T, typeof(value)}` になります。

isbits 型の場合、提供されていない場合はランダムまたは妥当な sentinel が試みられます。非 isbits の場合、`#undef` が sentinel として使用されます。提供されていない場合のデフォルト値は `missing` です。

`SentinelArray` では、要素を `value` に設定することができ、これによりラップされた配列に `sentinel` が保存されます。

isbits 要素型の場合、`SentinelArray` の現在の sentinel 値で `setindex!` 操作が試みられると、ラップされた配列に既に存在しない別の sentinel を選択しようとします。別の sentinel が見つからない場合（つまり、値がすでにラップされた配列に存在する場合）、エラーがスローされます。

**注意事項**:

  * 浮動小数点および日付/時刻型の場合、意味のある *実* 値を持たない妥当な sentinel が存在するため、デフォルトの sentinel を使用することをお勧めします
  * `Integer` 型の場合、すべてのビットパターンが有効であるため、ランダムな値が選択されます。使用が型範囲に対して非常に高いカーディナリティを伴う場合は、代わりに `Vector{Union{T, Missing}}` の使用を検討してください
  * `SentinelArray` には、可能な sentinel が存在しないため、プレーンな `Bool` 要素を持つことは許可されていません
  * `SentinelArray` は、`setindex!` と潜在的な sentinel 衝突に依存する使用時に *スレッドセーフではありません*（別の値に自動的にサイクルするためのチェックがあるため）。これは通常、sentinel 衝突の可能性が最も高い小さな `Integer` 要素型にのみ影響します
  * `SentinelArray` の生データへのアクセスは `parent(A)` または `pointer(A)` を介して可能ですが、生データは sentinel=>value のセマンティクスを *尊重しません*。つまり、生データには sentinel 値のエントリが含まれている可能性があります。

使用例:

  * 可能であれば、`SentinelArray` の代わりに `Vector{Union{T, typeof(value}}` を使用することを一般的にお勧めします
  * 現在、`convert(Vector{T}, A::Vector{Union{T, Missing}})` のような非コピー操作は不可能ですが、`missing` 値が存在しないことがわかっている場合でも、`SentinelArray` はストレージ配列を「アンラップ」することでこの操作を可能にします。例えば `parent(A)` のように
  * 現在、`Mmap.mmap` で `Vector{Union{T, Missing}}` を使用することもできません。`SentinelArray` を使用すると、親配列をディスクに書き込み、その後 `SentinelArray(Mmap.mmap(array_type, file))` を行うことができます（デフォルトの sentinel/value を使用することを前提としています）

例:

```julia
# デフォルトの sentinel/value で新しい SentinelArray を初期化
A = SentinelVector{Float64}(undef, 10)

# 既存の配列をラップし、手動で sentinel/value を提供
parent = zeros(UInt8, 10)
B = SentinelArray(parent, typemax(UInt8), nothing)
```
