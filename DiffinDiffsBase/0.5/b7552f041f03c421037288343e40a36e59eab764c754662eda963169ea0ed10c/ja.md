```
TermSet <: AbstractSet{AbstractTerm}
```

`Set{AbstractTerm}`をラップしたもので、項のコレクションを指定します。`Set`の一般的に使用されるメソッドは、`TermSet`でも同様に機能します。

`StatsModels.TermOrTerms`と比較すると、項の順序を保持しませんが、動的に構築された項により適しています。
