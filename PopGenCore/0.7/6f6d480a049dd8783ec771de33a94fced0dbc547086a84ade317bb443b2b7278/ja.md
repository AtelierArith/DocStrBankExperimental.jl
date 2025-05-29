```
ishet(locus::T) where T <: GenoArray
ishet(locus::Genotype)
ishet(locus::Missing)
```

ローカスまたはローカスがヘテロ接合体であるかどうかをテストする一連のメソッドであり、ヘテロ接合体であれば `true` を返し、そうでなければ（または欠損している場合） `false` を返します。計算には、遺伝子型が `missing` の場合に `missing` を返す `_ishet()` の使用をお勧めします。ベクトル版は、関数を要素にマッピングするだけです。
