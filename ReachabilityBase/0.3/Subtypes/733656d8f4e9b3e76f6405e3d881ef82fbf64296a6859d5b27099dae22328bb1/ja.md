```
subtypes(atype, concrete::Bool)
```

与えられた抽象型のサブタイプを返します。

### 入力

  * `atype`    – 抽象型
  * `concrete` – `true` の場合、具体的なサブタイプ（型階層の葉）だけを返します。それ以外の場合は、直接のサブタイプのみを返します。

### 出力

抽象型 `atype` のサブタイプのリストを、アルファベット順にソートして返します。

### 例

`Integer` 型を考えてみましょう。`concrete = false` を渡すと、実装は引数なしの `Base.subtypes` を模倣します。

```jldoctest subtypes
julia> using ReachabilityBase.Subtypes

julia> subtypes(Integer, false)
3-element Vector{Any}:
 Bool
 Signed
 Unsigned
```

`concrete = true` を渡すと、具体的なサブタイプを取得します。

```jldoctest subtypes
julia> subtypes(Integer, true)
12-element Vector{Type}:
 BigInt
 Bool
 Int128
 Int16
 Int32
 Int64
 Int8
 UInt128
 UInt16
 UInt32
 UInt64
 UInt8
```
