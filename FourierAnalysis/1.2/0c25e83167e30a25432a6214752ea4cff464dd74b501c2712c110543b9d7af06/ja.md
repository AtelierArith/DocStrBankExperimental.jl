```julia
function sameParams(𝐒        :: FDobjectsVector,
                    funcname :: String)
```

すべてのオブジェクトが同じ `sr`、`wl`、`DC`、`taper`、`func`（[SpectraVector](@ref) オブジェクトのみ）、`nonlinear`（[CrossSpectraVector](@ref) および [CoherenceVector](@ref) のみ）、および `smoothing` フィールドを持っている場合は true を返します。そうでない場合は、すべてのオブジェクトで同一でない最初のフィールドを指摘するエラーメッセージを印刷し、`Nothing` を返します。このメソッドはすべての [FDobjectsVector](@ref) タイプ、すなわち [SpectraVector](@ref)、[CrossSpectraVector](@ref) および [CoherenceVector](@ref) に適用されます。

`funcname` はユーザーが提供できるオプションの文字列です。エラーメッセージに挿入され、エラーを生成したコードの部分を特定します。デフォルトでは "unknown" が使用されます。
