```
MutableSmallDict{N,K,V} <: AbstractSmallDict{N,K,V}

MutableSmallDict{N,K,V}()
MutableSmallDict{N,K,V}(itr; unique = itr isa AbstractDict)
MutableSmallDict{N,K,V}(key1 => val1, key2 => val2, ...; unique = false)
```

キーの型 `K` と値の型 `V` を持ち、最大 `N` エントリを格納できる辞書です。この辞書は可変で、Julia の辞書インターフェースを実装しています。

キーと値の型が省略された場合、それらはペアから推測されるか、可能であればイテレータから推測されます。`unique` が `true` に設定されている場合、`itr` の要素は異なるキーを持つと仮定されます。

関連情報は [`AbstractSmallDict`](@ref)、[`SmallDict`](@ref) を参照してください。

# 例

```jldoctest
julia> d = MutableSmallDict{8}('a' => 0, 'b' => 1, 'c' => 4)
MutableSmallDict{8, Char, Int64} with 3 entries:
  'a' => 0
  'b' => 1
  'c' => 4


julia> delete!(d, 'b')
MutableSmallDict{8, Char, Int64} with 2 entries:
  'a' => 0
  'c' => 4
```
