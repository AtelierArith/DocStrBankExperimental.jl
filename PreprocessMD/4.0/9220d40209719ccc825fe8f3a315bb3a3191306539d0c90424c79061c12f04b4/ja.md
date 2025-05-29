Function -> Generate*cohort Inputs  Col*name -> 列名 domain_table -> あなたの概念に基づくケーステーブルの例条件、観察、薬、測定 concepts -> あなたが研究したい概念IDのリスト Output 研究したいコホート内のユニークな人物IDのリスト

# 例

```jldoctest
julia> using DataFrames

julia> df_condition_occurrence = DataFrame(condition_occurrence_id=[123, 5433, 8765, 12345, 6457, 62898], person_id = [1, 2, 3, 4, 5, 6], condition_concept_id = [196523, 436659, 435515, 436096, 440383, 37311319])
6×3 DataFrame
 Row │ condition_occurrence_id  person_id  condition_concept_id
     │ Int64                    Int64      Int64
─────┼──────────────────────────────────────────────────────────
   1 │                     123          1                196523
   2 │                    5433          2                436659
   3 │                    8765          3                435515
   4 │                   12345          4                436096
   5 │                    6457          5                440383
   6 │                   62898          6              37311319

julia> concepts = [196523, 436659, 435515, 436096, 440383]
5-element Vector{Int64}:
 196523
 436659
 435515
 436096
 440383

julia> result = generate_cohort( :condition_concept_id, df_condition_occurrence, concepts)
5-element Vector{Int64}:
 1
 2
 3
 4
 5

```
