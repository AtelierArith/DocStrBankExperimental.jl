```
Covers{T} <: DE9IMPredicate{T}

Covers(b)
Covers()
```

Covers: ジオメトリ A はジオメトリ B をカバーする場合、A と B の交差が B に等しい場合に限ります。

A Covers プレディケートは、2 つのジオメトリの交差が 2 番目のジオメトリに等しい場合に true を返します。

`Covers` がプレディケート関数に渡されたオブジェクトをラップする場合、それは 2 番目の引数 B でなければなりません。
