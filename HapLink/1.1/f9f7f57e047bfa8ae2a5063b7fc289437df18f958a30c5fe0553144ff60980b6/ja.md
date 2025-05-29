```
function ishaplotype(
    haplotype::Union{AbstractArray{Variation{S,T}}, Haplotype{S,T}},
    reads::AbstractArray{Haplotype{S,T}};
    frequency::Union{Float64,Nothing}=nothing,
    significance::Union{Float64,Nothing}=nothing,
    depth::Union{Int,Nothing}=nothing,
) where {S<:BioSequence,T<:BioSymbol}
```

`haplotype` の呼び出しが、提供されたキーワード基準に基づいて `reads` 内の配列によってサポートされているかどうかを判断します。

# 引数

  * `haplotype::Union{AbstractArray{Variation}, Haplotype}`: ハプロタイプとして検索する `Variation` の `Vector` または `Haplotype`
  * `reads::AbstractArray{Haplotype}`: `haplotype` を検索するためのリード

# キーワード

  * `frequency::Union{Float64,Nothing}=nothing`: `true` を返すために、`reads` 内で `haplotype` 全体が出現する最小回数
  * `significance::Union{Float64,Nothing}=nothing`: ハプロタイプが `true` を返すために超えなければならない連鎖不平衡の $χ^2$ 有意水準 ($α$)
  * `depth::Union{Int,Nothing}=nothing`: `true` を返すために、`reads` 内で `haplotype` 全体が出現する最小回数

# 拡張ヘルプ

連鎖不平衡 ($Δ$) は次のように計算されます。

$$
Δ = P_{reference} - \prod_i P_{ref,i}
$$

ここで

  * $$
    P_{reference}
    $$

    は、参照（コンセンサス）塩基のみを含むリードを見つける確率
  * $$
    P_{ref,i}
    $$

    は、ハプロタイプ内の変異 $i$ に対して参照（コンセンサス）塩基を含むリードを見つける確率

$$
χ^2
$$

統計量は次のように計算されます。

$$
χ^2 = \frac{
            Δ^2 n
        }
        {
            \left(\prod_i^N {P_{ref,i} \left(1 - P_{ref,i}\right)}\right)^\frac{2}{N}
        }
$$

ここで

  * $$
    N
    $$

    は `haplotype` 内の `Variation` の数（すなわち `length(haplotype)`）
  * $$
    n
    $$

    はサンプリングされたリードの総数（すなわち `length(reads)`）

有意性は累積 $χ^2$ 分布関数から計算されます。
