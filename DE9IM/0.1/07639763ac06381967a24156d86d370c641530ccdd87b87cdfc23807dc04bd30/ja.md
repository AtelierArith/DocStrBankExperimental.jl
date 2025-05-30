```
Within{T} <: DE9IMPredicate{T}

Within(b)
Within() = Within(nothing)
```

`Within`: 幾何学 A は幾何学 B の内部にすべての点がある場合に限り、幾何学 A は幾何学 B の内部にあります。

`Within` 述語は、最初の幾何学のすべての点が2番目の幾何学の内部にある場合に真を返します。

`Within` が述語関数に渡されたオブジェクトをラップする場合、それは2番目の引数 B でなければなりません。
