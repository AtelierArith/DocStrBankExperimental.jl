```
typetree(io=stdout, T)
```

型階層ツリーを印刷します。

型 `T` に対して、次のことを印刷します。

  * `T` のすべてのサブタイプを再帰的に
  * `Any` までの `T` のスーパタイプ
  * `T` のブランチを除いて、スーパタイプの子供の型ツリーは折りたたまれますが、子供が n > 0 の場合は `(n children)` という視覚的な手がかりで注釈が付けられます
  * `Any` の子供は隠され、`(other children are hidden)` という注釈が付けられ、多くの型が印刷されるのを避けます
  * 型 `T` は赤で強調表示されます

# 例

```julia
julia> using PrintTypeTree
julia> typetree(Integer)
julia> # `Integer` が赤で強調表示されることに注意してください
Any (other children are hidden)
└─ Number    
   ├─ Base.MultiplicativeInverses.MultiplicativeInverse (2 children)    
   ├─ Complex    
   └─ Real       
      ├─ AbstractFloat (5 children)       
      ├─ AbstractIrrational (1 children)       
      ├─ Integer       
      │  ├─ Bool       
      │  ├─ Signed       
      │  │  ├─ BigInt       
      │  │  ├─ Int128       
      │  │  ├─ Int16       
      │  │  ├─ Int32       
      │  │  ├─ Int64       
      │  │  └─ Int8       
      │  └─ Unsigned       
      │     ├─ UInt128       
      │     ├─ UInt16       
      │     ├─ UInt32       
      │     ├─ UInt64       
      │     └─ UInt8       
      └─ Rational
```
