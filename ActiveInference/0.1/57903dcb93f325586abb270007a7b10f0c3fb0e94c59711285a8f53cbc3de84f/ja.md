```
create_matrix_templates(n_states::Vector{Int64}, n_observations::Vector{Int64}, n_controls::Vector{Int64}, policy_length::Int64, template_type::String = "uniform")
```

指定されたパラメータに基づいて、A、B、C、D、およびE行列のテンプレートを作成します。

# 引数

  * `n_states::Vector{Int64}`: 次元と状態の数を指定するベクター。
  * `n_observations::Vector{Int64}`: 次元と観測の数を指定するベクター。
  * `n_controls::Vector{Int64}`: 各因子ごとの制御の数を指定するベクター。
  * `policy_length::Int64`: ポリシーシーケンスの長さ。
  * `template_type::String`: 作成するテンプレートのタイプ。 "uniform"、"random"、または "zeros" のいずれか。デフォルトは "uniform"。

# 戻り値

  * `A, B, C, D, E`: 行列とベクターとしての生成モデル。
