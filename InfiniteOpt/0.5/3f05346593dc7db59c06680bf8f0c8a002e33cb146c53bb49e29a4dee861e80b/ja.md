```
InfiniteVariable{F <: Function, VT <: VectorTuple} <: JuMP.AbstractVariable
```

コア無限変数情報を格納するための `DataType` です。同じ依存パラメータグループを参照するインデックスは、同じタプル要素内にある必要があります。`info.start` には、与えられた無限パラメータサポートの開始値を生成する開始値関数が含まれていることに注意することが重要です。この関数は、`is_vector_start = false` の場合はユーザーフォーマットを使用してサポートを開始値にマッピングする必要があります。それ以外の場合は、単一のサポートベクトルを入力としてマッピングを行う必要があります。

**フィールド**

  * `info::JuMP.VariableInfo{Float64, Float64, Float64, F}`: JuMP 変数情報。ここでの開始値は、パラメータ値を開始値にマッピングする関数です。
  * `parameter_refs::VT`: 変数をパラメータ化する無限パラメータ参照。
  * `parameter_nums::Vector{Int}`: `parameter_refs` のパラメータ番号。
  * `object_nums::Vector{Int}`: `parameter_refs` に関連付けられたパラメータオブジェクト番号。
  * `is_vector_start::Bool`: 開始関数はベクトルとしてフォーマットされたサポート値を取りますか？
