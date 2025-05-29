```
CrossEntropy(b)
```

関数を返します

$$
f(x) = -\frac{1}{N} \sum_{i = 1}^{N} b_i \log (x_i)+(1-b_i) \log (1-x_i),
$$

ここで `b` は長さ `N` の配列であり、各成分について `0 ≤ b ≤ 1` です。
