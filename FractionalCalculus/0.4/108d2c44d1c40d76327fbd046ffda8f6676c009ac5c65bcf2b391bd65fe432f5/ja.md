# リーズの意味におけるオルティゲイラの定義の分数導関数

```
fracdiff(f, α, end_point, h, RieszOrtigueira())
```

オルティゲイラによる中心差分を用いた対称リーズ導関数の定義

### 使用法

```julia-repl
julia> fracdiff(x->x, 0.5, 1, 0.01, RieszOrtigueira())
```
