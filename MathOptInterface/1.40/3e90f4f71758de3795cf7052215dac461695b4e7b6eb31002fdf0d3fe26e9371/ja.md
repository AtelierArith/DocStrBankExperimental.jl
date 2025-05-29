```
NEARLY_INFEASIBILITY_CERTIFICATE::ResultStatusCode
```

[`ResultStatusCode`](@ref) 列挙型のインスタンスです。

## 概要

結果は、不可能性の証明書に対する緩和基準を満たしています。

もし [`PrimalStatus`](@ref) が [`NEARLY_INFEASIBILITY_CERTIFICATE`](@ref) であれば、プライマル結果ベクトルはデュアル不可能性の証明書です。

もし [`DualStatus`](@ref) が [`NEARLY_INFEASIBILITY_CERTIFICATE`](@ref) であれば、デュアル結果ベクトルはプライマル不可能性の証明です。
