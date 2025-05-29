```
windowed(rmat, f, width, step = 1; kwargs...)
```

与えられた再発行行列 `rmat` のウィンドウビューに、与えられたウィンドウ `width` と `step` で RQA 関数 `f`（例えば `determinism`）を適用する便利な関数です。`kwargs...` は呼び出し `f(rmat_view; kwargs...)` に伝播されます。
