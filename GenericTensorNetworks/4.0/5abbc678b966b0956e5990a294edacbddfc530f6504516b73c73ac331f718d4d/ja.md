```
SumProductTree{ET} <: AbstractSetNumber
```

ツリーにエンコードされた構成列挙子であり、これはサムプロダクトネットワークによって与えられる最も自然な表現であり、構成をベクターに入れるよりもメモリ効率が良いことが多い。このツリー構造から構成を効率的にサンプリングするには、[`generate_samples`](@ref)を使用することができる。

## フィールド

  * `tag` は `ZERO`、`ONE`、`LEAF`、`SUM`、`PROD` のいずれかです。
  * `data` は `LEAF` ノードに格納されている要素です。
  * `left` と `right` は `SUM` または `PROD` ノードの2つのオペランドです。

## 例

```jldoctest; setup=:(using GenericTensorNetworks)
julia> s = SumProductTree(bv"00111")
00111


julia> q = SumProductTree(bv"10000")
10000


julia> x = s + q
+ (count = 2.0)
├─ 00111
└─ 10000


julia> y = x * x
* (count = 4.0)
├─ + (count = 2.0)
│  ├─ 00111
│  └─ 10000
└─ + (count = 2.0)
   ├─ 00111
   └─ 10000


julia> collect(y)
4-element Vector{StaticBitVector{5, 1}}:
 00111
 10111
 10111
 10000

julia> zero(s)
∅



julia> one(s)
00000


```
