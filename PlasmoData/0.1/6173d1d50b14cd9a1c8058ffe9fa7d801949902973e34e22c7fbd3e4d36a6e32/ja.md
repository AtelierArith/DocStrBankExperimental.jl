```
DataGraph{T, T1, T2, T3, M1, M2}()
DataGraph()
```

空の DataGraph オブジェクトを初期化するためのコンストラクタ。データ型は次のとおりです：T はインデックス用の整数型、T1、T2、および T3 はそれぞれノード、エッジ、およびグラフデータのデータ型、M1 <: AbstractMatrix{T1} はノードデータに対応し、M2 <: AbstractMatrix{T2} はエッジデータに対応します。

T、T1、T2、T3、M1、および M2 が定義されていない場合、デフォルトはそれぞれ `Int`、`Float64`、`Float64`、`Float64`、`Matrix{Float64}`、および `Matrix{Float64}` です。
