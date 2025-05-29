```
Derivative{F <: Function, V <: GeneralVariableRef} <: JuMP.AbstractVariable
```

コア無限微分情報を格納するための `DataType` です。これは次の形の微分に従います: $\frac{\partial x(\alpha, \hdots)}{\partial \alpha}$ ここで、$x(\alpha, \hdots)$ は無限変数であり、$\alpha$ は無限パラメータです。ここで、$x$ と $\alpha$ はスカラーでなければなりません。

`info.start` には、与えられた無限パラメータサポートの開始値を生成する開始値関数が含まれている必要があります。この関数は、`is_vector_start = false` の場合はユーザーフォーマットを使用してサポートを開始値にマッピングする必要があります。それ以外の場合は、単一のサポートベクトルを入力として使用してマッピングを行う必要があります。また、変数参照型 `V` は無限変数およびパラメータに関連している必要があります。

**フィールド**

  * `info::JuMP.VariableInfo{Float64, Float64, Float64, F}`: JuMP 変数情報。
  * `is_vector_start::Bool`: 開始関数はベクトルとしてフォーマットされたサポート値を取りますか？
  * `variable_ref::V`: 無限変数引数の変数参照。
  * `parameter_ref::V`: 微分演算子を定義する無限パラメータの変数参照。
