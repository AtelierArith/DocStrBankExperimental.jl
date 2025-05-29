```
sparsity(sym_func::AbstractArray{<:Node})
```

配列表現のスパース性を表す数値を計算します。`nelts`が配列内の要素数で、`nzeros`が配列内のゼロ要素の数である場合、`sparsity = (nelts-nzeros)/nelts` となります。

通常、`make_function`への呼び出しと組み合わせて使用され、キーワード引数`init_with_zeros`をfalseに設定するかどうかを判断します。
