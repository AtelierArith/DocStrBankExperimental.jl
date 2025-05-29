```
siteind(::typeof(first), M::Union{MPS,MPO}, j::Integer; kwargs...)
```

MPSまたはMPOで見つかった最初のサイトインデックスを返します（`j`番目のMPS/MPOテンソルに固有の最初のインデックス）。

`kwargs`を使用して、素数レベルやタグなど、異なるフィルターを選択できます。
