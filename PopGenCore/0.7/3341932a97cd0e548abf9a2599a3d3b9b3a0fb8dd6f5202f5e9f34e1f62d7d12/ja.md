```
ishom(locus::T) where T <: GenoArray
ishom(locus::T) where T<:Base.SkipMissing
ishom(locus::Genotype)
ishom(locus::Missing)
```

ローカスまたはローカスがホモ接合体であるかどうかをテストし、ホモ接合体であれば `true` を返し、そうでなければ（または欠損の場合） `false` を返す一連のメソッドです。計算には、遺伝子型が `missing` の場合に `missing` を返す `_ishom()` の使用をお勧めします。ベクトルメソッドは、単に関数を要素に適用します。単相遺伝子型は `false` を返します。
