`pp = QuadraticProgram(A, b, C, d, z=zeros(..), P=I; kwargs...)`     問題のタイプ     `min_x 1/2xᵀPx + zᵀx, s.t Ax=b, Cx≤d`     ここで `P` は正定値です。

```
キーワード引数:
`semidefinite=true` 双対が半正定値である可能性があることを示し、反復的な精緻化を可能にします
`ϵ = sqrt(eps(T))`  反復的な精緻化で使用される緩和 (H+ϵI)
`smartstart=true`   初期のアクティブセットに対するスマートな推測を有効にします
`scaling=true`      制約を単位行ノルムにスケーリングします

保存: `A,b,C,d,z,P,PF,sol,boxQP` およびいくつかの一時変数。
`sol` は `solve!(qp)` を呼び出した後の解です、
`PF` は `P` の因子分解です、
`boxQP::BoxConstrainedQP` は二次コストを持つ解決すべき双対問題を表します
`G=[A*P⁻¹*A' A*P⁻¹*C'; C*P⁻¹*A' C*P⁻¹*C']`,
線形コスト `c = [A*z + b; C*z+d]`,
および制約 `0≤xᵢ ∀i>size(A,1)` です。
```
