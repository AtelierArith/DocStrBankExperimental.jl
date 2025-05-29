```
SmallDict{N,K,V} <: AbstractSmallDict{N,K,V}

SmallDict{N,K,V}()
SmallDict{N,K,V}(itr; unique = itr isa AbstractDict)
SmallDict{N,K,V}(key1 => val1, key2 => val2, ...; unique = false)
```

キータイプ `K` と値タイプ `V` を持ち、最大 `N` エントリを格納できる不変辞書です。すべてのエントリは、構築時に提供されたキー-値イテレータ `itr` から、または明示的に与えられたペアから来ます。

キーと値のタイプが省略された場合、それらはペアから推測されるか、可能であればイテレータから推測されます。`unique` が `true` に設定されている場合、`itr` の要素は異なるキーを持つと仮定されます。

詳細は [`AbstractSmallDict`](@ref)、[`MutableSmallDict`](@ref) を参照してください。

# 例

```jldoctest
julia> SmallDict{8}(Int16(1) => 2, Int32(3) => 4.0)
SmallDict{8, Int32, Float64} with 2 entries:
  1 => 2.0
  3 => 4.0

julia> SmallDict{8,Char,Int}('a'+k => k^2 for k in 0:2; unique = true)
SmallDict{8, Char, Int64} with 3 entries:
  'a' => 0
  'b' => 1
  'c' => 4
```
