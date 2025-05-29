```julia
struct BVHTraversal{C1<:(AbstractVector), C2<:(AbstractVector)}
```

収集されたBVHトラバーサルの`contacts`ベクター、いくつかの統計、および将来のトラバーサルに再利用できる2つのバッファ`cache1`と`cache2`が含まれ、メモリ割り当てを最小限に抑えます。

# フィールド

  * `start_level1::Int`: 最初のBVHの単一/ペアツリーのトラバーサルが開始されたレベル。
  * `start_level2::Int`: 2番目のBVHのペアツリーのトラバーサルが開始されたレベル。
  * `num_checks::Int`: 行われた接触チェックの総数。
  * `num_contacts::Int`: 見つかった接触の数。
  * `contacts::view(cache1, 1:num_contacts)`: `cache1`へのビューとして見つかった接触ペア。
  * `cache1::C1{IndexPair} <: AbstractVector`: 最初のBVHトラバーサルバッファ。
  * `cache2::C2{IndexPair} <: AbstractVector`: 2番目のBVHトラバーサルバッファ。

```
