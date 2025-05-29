```
interpolate_and_bin(
        left_bin_edges::AbstractRange{T2}, xs, ys, 
        intp::Linear, intp_grid::AbstractRange{T1}, 
         extrapolation_bc::Union{<:Real, Interpolations.BoundaryCondition}
        f::Function, args...; kwargs...) where {T1, T2}
```

`xs` と `ys` を `intp_grid` に線形補間し、その後 `N` 要素の `left_bin_edges` グリッドで定義されたグリッド上で補間されたデータをビンに分けます。ビン分けの後、各ビンに対して引数 `args` とキーワード引数 `kwargs` を使って `f` を要素ごとに適用します。`N-1` のビン要約のベクトルを返します。

## 詳細

ビン分けは、`xs` と `ys` を `intp_grid` に補間した *後* に行われます。ビン分けは、`intp_grid` の値を `left_bin_edges` で定義されたビンに分配することによって行われます。つまり、`intp_grid[i]` が `k` 番目のビンに入る場合、`intp(xs)[i]` は `k` 番目のビンに割り当てられます。`left_bin_edges` に `N` グリッドポイントが含まれている場合、合計で `N - 1` のビンがあります。

`xs` に `NaN` 値が含まれている場合、これらは提供された `intp_grid` に補間する *前* に線形補間によって内部的に埋められます。
