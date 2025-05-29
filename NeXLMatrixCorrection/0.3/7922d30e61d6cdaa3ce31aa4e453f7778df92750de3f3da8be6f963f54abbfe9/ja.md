`import DataFrame`が必要です。

```
detail(unk::MultiZAF, std::MultiZAF, θunk::AbstractFloat, θstd::AbstractFloat)::DataFrame

detail(mzs::AbstractArray{Tuple{MultiZAF,MultiZAF}}, θunk::AbstractFloat, θstd::AbstractFloat)
```

`DataFrame`内の`MultiZAF`行列補正の各項を表形式で表示します。
