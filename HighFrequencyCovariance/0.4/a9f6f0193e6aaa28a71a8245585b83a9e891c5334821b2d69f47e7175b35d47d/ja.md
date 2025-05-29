```
DataFrames.DataFrame(
    covar::CovarianceMatrix,
    othercols::Dict = Dict{Symbol,Any}();
    delete_duplicate_correlations::Bool = true,
)
```

CovarianceMatrixを`DataFrame`形式に変換します。

### 入力

  * `covar` - `CovarianceMatrix`
  * `othercols` - これにより`DataFrame`に列が追加されます。例えば、`Dict{Symbol,String}([:pc] .=> ["Fred's PC"])`の場合、この推定がFredのPCで行われたことを示す列が追加されます。
  * `delete_duplicate_correlations` - 不要な相関を含めるべきかどうか（相関行列は対称であるため、半分のエントリは情報を重複させます）。

### 戻り値

  * `DataFrame`。
