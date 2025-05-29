```
LazySum{O} <: AbstractVector{O}
```

必要なときにのみ明示的な合計が行われる遅延合計を表す型。この型は基本的に、効率的に計算するためのいくつかの追加機能を持つ `AbstractVector` です。

## フィールド

  * ops – 合計可能なオブジェクトのベクター

---

## コンストラクタ

```
LazySum(x::Vector)
```
