```
multiple_target_state_extraction(b::GaussianMixture, th::Real)
```

重み (x.w) が閾値を超えるターゲットを抽出します。

引数:     `b::GaussianMixture`: ガウス混合のセット     `th::Real`: 重みに対する閾値。この閾値を超える場合、     状態推定が抽出されます。

返り値:     X: マルチターゲット状態推定 ```
