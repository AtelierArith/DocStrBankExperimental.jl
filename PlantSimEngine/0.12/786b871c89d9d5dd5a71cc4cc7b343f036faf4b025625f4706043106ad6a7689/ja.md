```
ModelList(models::M, status::S)
ModelList(;
    status=nothing,
    type_promotion=nothing,
    variables_check=true,
    kwargs...
)
```

シミュレーションのためのモデルをリストし（`models`）、変数の初期化、型の昇格、時間ステップの処理のためのすべてのボイラープレートを行います。

!!! note
    ステータスフィールドは入力モデルに依存します。モデルのインスタンス化時に[`variables`](@ref)を使用して、モデルに必要な変数を取得できます。また、[`inputs`](@ref)や[`outputs`](@ref)を使用することもできます。


# 引数

  * `models`: モデルのリスト。通常は`NamedTuple`として与えられますが、`getproperty`を実装する他の構造体でもかまいません。
  * `status`: モデルの変数の初期化を含む構造体。通常はkwargとして与えられるときはNamedTupleで、または`Tables.jl`のTablesインターフェースを実装する任意の構造体（*例*：DataFrame、詳細は参照）です。
  * `type_promotion`: 変数のオプションの型変換で、デフォルト値は`nothing`です。すなわち、変換は行われません。ユーザーが`kwargs`として入力した変数には変換が適用されないことに注意してください（手動で行う必要があります）。現在の型をキー、新しい型を値とするDictとして提供する必要があります。
  * `variables_check=true`: ユーザーによってすべての必要な変数が初期化されているかを確認します。
  * `kwargs`: モデルで、シミュレートするプロセスの名前が付けられています。

# 詳細

ステータスにカスタム型を入力し、ユーザーが入力時に`status`フィールドを部分的に初期化できるようにする必要がある場合は、`add_model_vars!`のメソッドを実装する必要があります。この関数は、モデルの変数を型に追加し、完全に初期化されていない場合に使用されます。デフォルトのメソッドは、`Tables.jl`インターフェース（*例*：DataFrame）および`NamedTuples`を実装する任意の型と互換性があります。

`ModelList`は、必要なすべての変数がリストされていない場合、入力`status`のコピーを作成します。

## 例

パッケージの例フォルダにある`dummy.jl`からダミーモデルを使用します。これは、`Process1Model`、`Process2Model`、`Process3Model`の3つのダミープロセスを実装し、それぞれに1つのモデル実装があります：`Process1Model`、`Process2Model`、`Process3Model`。

```jldoctest 1
julia> using PlantSimEngine;
```

例のプロセスとモデルを含めます：

```jldoctest 1
julia> using PlantSimEngine.Examples;
```

```jldoctest 1
julia> models = ModelList(process1=Process1Model(1.0), process2=Process2Model(), process3=Process3Model());
[ Info: シミュレーションの前に初期化する必要がある変数があります: (process1 = (:var1, :var2), process2 = (:var1,)) (see `to_initialize()`)
```

```jldoctest 1
julia> typeof(models)
ModelList{@NamedTuple{process1::Process1Model, process2::Process2Model, process3::Process3Model}, Status{(:var5, :var4, :var6, :var1, :var3, :var2), NTuple{6, Base.RefValue{Float64}}}}
```

キーワード引数として変数が与えられていないため、ModelListのステータスはまだ設定されておらず、すべての変数は入力と出力で与えられたデフォルト値（通常は`typemin(Type)`、すなわち浮動小数点数の場合は`-Inf`）に初期化されています。このコンポーネントはまだシミュレーションできません。

シミュレーションのために初期化する必要がある変数を知るために、[`to_initialize`](@ref)を使用します：

```jldoctest 1
julia> to_initialize(models)
(process1 = (:var1, :var2), process2 = (:var1,))
```

これで、`status`フィールドにこれらの変数の値を提供し、`ModelList`をシミュレートできます。*例*として`process3`（`process1`と`process2`に結合）をシミュレートします：

```jldoctest 1
julia> models = ModelList(process1=Process1Model(1.0), process2=Process2Model(), process3=Process3Model(), status=(var1=15.0, var2=0.3));
```

```jldoctest 1
julia> meteo = Atmosphere(T = 22.0, Wind = 0.8333, P = 101.325, Rh = 0.4490995);
```

```jldoctest 1
julia> outputs_sim = run!(models,meteo)
TimeStepTable{Status{(:var5, :var4, :var6, ...}(1 x 6):
╭─────┬─────────┬─────────┬─────────┬─────────┬─────────┬─────────╮
│ Row │    var5 │    var4 │    var6 │    var1 │    var3 │    var2 │
│     │ Float64 │ Float64 │ Float64 │ Float64 │ Float64 │ Float64 │
├─────┼─────────┼─────────┼─────────┼─────────┼─────────┼─────────┤
│   1 │ 36.0139 │    22.0 │ 58.0139 │    15.0 │     5.5 │     0.3 │
╰─────┴─────────┴─────────┴─────────┴─────────┴─────────┴─────────╯
```

```jldoctest 1
julia> outputs_sim[:var6]
1-element Vector{Float64}:
 58.0138985
```

変数に特別な型を使用したい場合は、`type_promotion`引数を使用できます：

```jldoctest 1
julia> models = ModelList(process1=Process1Model(1.0), process2=Process2Model(), process3=Process3Model(), status=(var1=15.0, var2=0.3), type_promotion = Dict(Float64 => Float32));
```

`type_promotion`を使用して、ステータスをFloat32に強制しました：

```jldoctest 1
julia> [typeof(models[i][1]) for i in keys(status(models))]
6-element Vector{DataType}:
 Float32
 Float32
 Float32
 Float64
 Float64
 Float32
```

しかし、デフォルトの変数（ステータス引数で与えられていない変数）のみがFloat32に変換されたことがわかります。提供された2つの変数は変換されませんでした。これは、ユーザーがステータスで提供する変数に任意の型を指定できるようにしたいためです。すべての変数をFloat32に変換したい場合は、Float32として渡すことができます：

```jldoctest 1
julia> models = ModelList(process1=Process1Model(1.0), process2=Process2Model(), process3=Process3Model(), status=(var1=15.0f0, var2=0.3f0), type_promotion = Dict(Float64 => Float32));
```

`type_promotion`を使用して、ステータスをFloat32に強制しました：

```jldoctest 1
julia> [typeof(models[i][1]) for i in keys(status(models))]
6-element Vector{DataType}:
 Float32
 Float32
 Float32
 Float32
 Float32
 Float32
```
