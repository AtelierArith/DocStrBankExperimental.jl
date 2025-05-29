フル情報最大尤度推定。欠損のある観測データを扱うことができます。

# コンストラクタ

```
SemFIML(;observed, specification, kwargs...)
```

# 引数

  * `observed::SemObservedMissing`: モデルの観測部分
  * `specification`: `RAMMatrices` または `ParameterTable` オブジェクトのいずれか

# 例

```julia
my_fiml = SemFIML(observed = my_observed, specification = my_parameter_table)
```

# インターフェース

解析的勾配が利用可能です。
