```
@hp(block)
```

定理の仮説を構築するためのマクロです。

### 入力

block – 定理の仮説を含む式で、単一の文または `begin...end` の間の文のシーケンスであることができます。

### 出力

`Hypothesis` 型のオブジェクト。

### 例

```jldoctest
julia> @hp O := Circle(A, B, C)
POINTS:
------------
A : free
B : free
C : free
O : dependent by (1)

HYPOTHESIS:
------------
(1) OA ≅ OB ≅ OC
```
