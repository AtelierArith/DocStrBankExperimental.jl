```
gather_array(val::Symbol, workers, dim=1; free=false)
```

`workers` にある値 `val` の配列を集めて配列にします。個々の配列は、指定された次元 `dim` に沿って結合されます。つまり、`dim=1` はおおよそ `vcat` を使用するのと同等であり、`dim=2` は `hcat` に相当します。

`val` は配列ベースの型でなければなりません。そうでない場合、関数は失敗します。

`free` が true の場合、集められた後に `val` は `unscatter` されます。

これは結果の配列を事前に割り当てるため、例えば `vcat` を使用した折りたたみのための `dmapreduce` よりも効率的です。
