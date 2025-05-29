```
@th(block)
```

定理の主張を構築するためのマクロ。

### 入力

block – 定理の主張を含む式で、単一の文または `begin...end` の間の文のシーケンスであることができます。

### 出力

`Thesis` 型のオブジェクト。

### 例

```jldoctest
julia> @th Segment(A, O) ≅ Segment(O, C)
THESIS:
------------
AO ≅ OC
```
