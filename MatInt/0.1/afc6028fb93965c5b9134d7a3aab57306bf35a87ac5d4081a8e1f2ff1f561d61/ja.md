`complementInt(full::Matrix{<:Integer}, sub::Matrix{<:Integer})`

`complementInt(sub::Matrix{<:Integer})`

`M`を`full`の整数行空間とし、`S`を`sub`の整数行空間とします。`S`は`M`の部分空間である必要があります。関数`complementInt`は、`S`を拡張する`M`の自由基底を計算します。つまり、`S`の次元が`n`である場合、`M`の基底`B={b₁,…,bₘ}`と、`n`個の整数`x₁,…,xₙ`を決定します。これにより、`n`個のベクトル`sᵢ:=xᵢ⋅bᵢ`が`S`の基底を形成します。引数が1つだけ与えられた場合、`full`は`size(sub,2)`のサイズの単位行列であると仮定されます。

関数`complementInt`は、以下のコンポーネントを持つ名前付きタプルを返します：

  * `complement` 行が`bₙ₊₁,…,bₘ`である行列。
  * `sub` 行が`sᵢ`（`S`の基底）である行列。
  * `moduli` 要素`xᵢ`。

```julia-repl
julia> n=[1 2 3;4 5 6]
2×3 Matrix{Int64}:
 1  2  3
 4  5  6

julia> complementInt(n)
(complement = [0 0 1], sub = [1 2 3; 0 3 6], moduli = [1, 3])
```
