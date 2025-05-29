```
divisors(n::Integer) -> Vector
```

正の約数のベクトルを `n` で返します。

素因数分解 `n = p₁^k₁ ⋯ pₘ^kₘ` を持つ非ゼロ整数 `n` に対して、`divisors(n)` は長さ (k₁ + 1)⋯(kₘ + 1) のベクトルを返し、`n` の約数を辞書順（数値順ではなく）で含みます。

`divisors(-n)` は `divisors(n)` と同等です。

便利のために、`divisors(0)` は `[]` を返します。

# 例

```jldoctest; filter = r"(\s+#.*)?"
julia> divisors(60)
12-element Vector{Int64}:
  1         # 1
  2         # 2
  4         # 2 * 2
  3         # 3
  6         # 3 * 2
 12         # 3 * 2 * 2
  5         # 5
 10         # 5 * 2
 20         # 5 * 2 * 2
 15         # 5 * 3
 30         # 5 * 3 * 2
 60         # 5 * 3 * 2 * 2

julia> divisors(-10)
4-element Vector{Int64}:
  1
  2
  5
 10

julia> divisors(0)
Int64[]
```
