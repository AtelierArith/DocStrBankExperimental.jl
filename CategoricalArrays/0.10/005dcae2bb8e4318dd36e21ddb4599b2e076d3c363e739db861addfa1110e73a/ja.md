```
cut(x::AbstractArray, ngroups::Integer;
    labels::Union{AbstractVector{<:AbstractString},Function},
    allowempty::Bool=false)
```

数値配列を `ngroups` 分位数に分割します。分位数は `quantile` を使用して決定されます。

`x` に `missing` 値が含まれている場合、分位数を計算する際に自動的にスキップされます。

# キーワード引数

  * `labels::Union{AbstractVector, Function}`: 区間に使用する名前を与える文字列、文字、または数値のベクトル; または、左端と右端の区間境界およびグループインデックスからラベルを生成する関数 `f(from, to, i; leftclosed, rightclosed)`。デフォルトは `"Qi: [from, to)"`（または最右の区間の場合は `"Qi: [from, to]"`）。
  * `allowempty::Bool=false`: `false` の場合、いくつかの分位数のブレークポイントが等しいとエラーが発生し、空の区間が生成されます; `true` の場合、重複したブレークが許可され、それによって生成される区間は未使用のレベルとして保持されます（ただし、重複したラベルは許可されません）。
