```
ApproximateTwoSampleKSTestElementWise(d1::UncertainDataset,
    d2::UncertainDataset, n::Int = 1000) -> Vector{ApproximateTwoSampleKSTest}
```

`d1` と `d2` が同じ数の不確実な観測値を含むと仮定すると、`d1` の各不確実な値の `n` 回の実現を引き出し、その後、`d2` の各不確実な値の `n` 回の実現を別々に引き出します。

次に、`d1` と `d2` の不確実な値が同じ分布から来ているという帰無仮説に対して、`d1` と `d2` の（要素ごとに）値が異なる分布から来ているという対立仮説の下で、漸近的二標本コルモゴロフ–スミルノフ検定を実施します。

テストはペアごとに実施されます。すなわち、`ApproximateTwoSampleKSTest(d1[i], d2[i])` が不確実な値の $i$ 番目のペアに対して `n` 回の引き出しを行います。 ```
