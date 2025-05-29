```
difference_of_means(x::AbstractArray)
```

`x`の前半と後半の平均の絶対差を返します。`difference_of_means`は、値の違いに焦点を当てた変化メトリックとして使用できます。`mean`の代わりに他のモーメントを使用して同様の統計的差異を作成するのは簡単です。実際、`difference_of_means`のソースは次のとおりです：

```julia
# 1ベースのインデックスを前提としています
n = length(x)
x1 = view(x, 1:n÷2)
x2 = view(x, (n÷2 + 1):n)
return abs(mean(x1) - mean(x2))
```

`difference_of_means`は、サイズ2のウィンドウにも適切に使用でき、その場合、変化メトリックのタイムシリーズは指標タイムシリーズの`abs.(diff(...))`と同じになります。
