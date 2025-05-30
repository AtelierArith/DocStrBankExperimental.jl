```
GPおよびSP変数のための変数情報構造。

GPVariableとSPVariableの間で共有される共通フィールドを含みます。

# フィールド

  * `index::Int`: モデル内での変数の一意の識別子
  * `name::String`: 変数名
  * `lower_bound::Union{Float64,Nothing}`: 下限（指定されている場合は正でなければならない）
  * `upper_bound::Union{Float64,Nothing}`: 上限（指定されている場合は正でなければならない）
  * `fixed_value::Union{Float64,Nothing}`: 固定値（指定されている場合は正でなければならない）
```
