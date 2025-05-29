```
struct FallbackRank{T,D,F} <: RankCheck
    tol::T
    default::D
    fallback::F
end
```

デフォルトでは、`default`を使用してランクをチェックし、[`doubt`](@ref)が`tol`よりも厳密に大きい場合は`fallback`にフォールバックします。デフォルトでは、`fallback`は[`UserRank`](@ref)です。

## 例

[`UserRank`](@ref)の利点は、ユーザーがランクチェックがあいまいであるかどうかを確認し、それに応じて行動できることです。欠点は、多くのランクチェックを行う必要がある場合に面倒になる可能性があることです。`FallbackRank`を使用すると、ユーザーは厄介なものだけを整理すれば済みます。以下の例では、最初の例は[`LargestDifferentialRank`](@ref)によって処理されます。2番目の例では、ユーザーはこれが厄介な選択であることを認識し、2つのランクのいずれかを手動で選択し、その値を使用してコードの残りの結果を確認し、次に別のランクを選択してこの異なる選択の影響を確認できます。

```julia
julia> check = FallbackRank(1e-1, LargestDifferentialRank())
FallbackRank{Float64, LargestDifferentialRank, UserRank}(0.1, LargestDifferentialRank(), UserRank(8))

julia> rank_from_singular_values([1, 1e-2, 5e-2, 1e-3, 1e-6, 5e-7], check)
4

julia> rank_from_singular_values([1, 1e-2, 5e-2, 1e-3, 5e-6, 5e-7], check)
最後の重要な特異値を選択してください：
 > 1.0
   0.01
   0.05
   0.001
   5.0e-6
   5.0e-7
1

julia> rank_from_singular_values([1, 1e-2, 5e-2, 1e-3, 5e-6, 5e-7], check)
最後の重要な特異値を選択してください：
   1.0
   0.01
   0.05
 > 0.001
   5.0e-6
   5.0e-7
4
```
