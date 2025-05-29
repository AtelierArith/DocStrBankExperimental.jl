```
consecutive_subspans(span::AlignedSpan, duration::Period; keep_last=true)
consecutive_subspans(span::AlignedSpan, n_window_samples::Int; keep_last=true)
```

`AlignedSpan` のイテレータを作成します。各 `AlignedSpan` は、元の `span` のインデックスをカバーする連続したインデックスを持ちます（`keep_last=true` の場合）。

`keep_last=true`（デフォルトの動作）の場合、最後のスパンは他のスパンよりもサンプル数が少ない可能性があります。

  * 各スパンは `n_window_samples` サンプルを持ちます（これは `duration` が `Period` の場合、`n_samples(span.sample_rate, duration)` として計算されます）、ただし最後のスパンは少ない可能性があります。
  * サブスパンの数は `cld(n_samples(span), n_window_samples)` で与えられます。
  * 最後のサブスパンのサンプル数は `r = rem(n_samples(span), n_window_samples)` ですが、`r=0` の場合は最後のサブスパンは他のスパンと同じサンプル数、すなわち `n_window_samples` を持ちます。
  * `span` のすべてのインデックスは、正確に1つのサブスパンによってカバーされることが保証されています。

`keep_last=false` の場合、すべてのスパンは同じ数のサンプルを持ちます：

  * 各スパンは `n_window_samples` サンプルを持ちます（これは `duration` が `Period` の場合、`n_samples(span.sample_rate, duration)` として計算されます）。
  * サブスパンの数は `fld(n_samples(span), n_window_samples)` で与えられます。
  * `span` のインデックスの最後の部分はカバーされない可能性があります（`n_window_samples` の長さの別のサブスパンを収められない場合）。
