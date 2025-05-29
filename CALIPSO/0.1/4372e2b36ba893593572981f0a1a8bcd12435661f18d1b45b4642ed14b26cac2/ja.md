```
Solver(methods, num_variables, num_parameters, num_equality, num_cone;
    parameters, nonnegative_indices, second_order_indices, custom, options)

CALIPSOソルバー

methods: ProblemMethods - 目的関数と制約関数、およびそれらの導関数を含む 
num_variables: Int - プライマル決定変数の次元 
num_parameters: Int - 問題データの次元 
num_equality: Int - 等式制約の次元 
num_cone: Int - コーン制約の次元 
parameters: Vector{Real} - 問題データ 
nonnegative_indices: Vector{Int} - 非負オルタンに対応するコーン制約のインデックス 
second_order_indices: Vector{Vector{Int}} - 二次コーンに対応するコーン制約のインデックス
custom: Any - ソルバーコールバックに使用されるユーザー提供型 
options: Options - ソルバー設定
```
