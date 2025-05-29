```
to_initialize(; verbose=true, vars...)
to_initialize(m::T)  where T <: ModelList
to_initialize(m::DependencyGraph)
to_initialize(mapping::Dict{String,T}, graph=nothing)
```

モデルとプロセスのセットを提供することで初期化する必要がある変数を返します。この関数はモデルの結合を考慮し、いくつかのモデルの出力としての変数が他のモデルの入力として使用されることを考慮して、必要な変数のみを返します。

# 引数

  * `verbose`: `true`の場合、情報メッセージを表示します。
  * `vars...`: 考慮するモデルとプロセス。
  * `m::T`: [`ModelList`](@ref)。
  * `m::DependencyGraph`: [`DependencyGraph`](@ref)。
  * `mapping::Dict{String,T}`: モデルを器官に関連付けるマッピング。
  * `graph`: 植物またはシーンを表すグラフ、*e.g.* マルチスケールツリーグラフ。グラフは、初期化されていない変数がグラフノードの属性に見つけられるかどうかを確認するために使用されます。

# 例

```@example
using PlantSimEngine

# パッケージ内の例として与えられたダミーモデルをロードします：
using PlantSimEngine.Examples

to_initialize(process1=Process1Model(1.0), process2=Process2Model())

# またはコンポーネントを直接使用：
models = ModelList(process1=Process1Model(1.0), process2=Process2Model())
to_initialize(models)

m = ModelList(
    (
        process1=Process1Model(1.0),
        process2=Process2Model()
    ),
    Status(var1 = 5.0, var2 = -Inf, var3 = -Inf, var4 = -Inf, var5 = -Inf)
)

to_initialize(m)
```

またはマッピングを使用：

```@example
using PlantSimEngine

# パッケージ内の例として与えられたダミーモデルをロードします：
using PlantSimEngine.Examples

mapping = Dict(
    "Leaf" => ModelList(
        process1=Process1Model(1.0),
        process2=Process2Model(),
        process3=Process3Model()
    ),
    "Internode" => ModelList(
        process1=Process1Model(1.0),
    )
)

to_initialize(mapping)
```
