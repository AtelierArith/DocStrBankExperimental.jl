```
MultiAssayExperiment(experiments, sampledata, samplemap, metadata = Dict{String,Any}())
```

コンポーネントから新しい `MultiAssayExperiment` を作成します。

`experiments` には、実験名と `SummarizedExperiment` オブジェクトの順序付きペアが含まれている必要があります。各 `SummarizedExperiment` には、行の数とアイデンティティに関して任意の数を含めることができます。ただし、列名は非ヌルであり、各オブジェクト内で一意でなければなりません。

`sampledata` の各行は概念的なサンプルに対応します。最初の列は `name` と呼ばれ、`Vector{String}` 内のサンプル名を含む必要があります。サンプル名は任意ですが、一意である必要があります。他の列は任意の数とタイプで提供でき、通常はサンプルレベルの注釈を含みます。

`samplemap` テーブルは、3つの `Vector{String}` 列 - `sample`、`experiment`、`colname` - を持ち、各概念的サンプルと特定の `SummarizedExperiment` の列との対応を指定することが期待されます。期待されるフォーマットの詳細については、[`setsamplemap!`](@ref) を参照してください。

`samplemap` 列の値は、相互参照されたターゲットとの1:1の一致を必要としません。片方またはもう片方に固有の値は、[`expandsampledata`](@ref) や [`filtersamplemap`](@ref) のようなメソッドでは無視されます。これにより、ユーザーは常に有効性チェックに引っかかることなく、オブジェクトを柔軟に操作できます。

`metadata` は、サンプルに関連しない他の注釈を保存します。

# 例

```jldoctest
julia> using MultiAssayExperiments

julia> using SummarizedExperiments

julia> exp = OrderedDict{String, SummarizedExperiment}();

julia> exp["foo"] = SummarizedExperiments.exampleobject(100, 2);

julia> exp["bar"] = SummarizedExperiments.exampleobject(50, 5);

julia> cd = DataFrame(
           name = ["Aaron", "Michael", "Jayaram", "Sebastien", "John"],
           disease = ["good", "bad", "good", "bad", "very bad"]
       );

julia> sm = DataFrame(
           sample = ["Aaron", "Michael", "Aaron", "Michael", "Jayaram", "Sebastien", "John"],
           experiment = ["foo", "foo", "bar", "bar", "bar", "bar", "bar"],
           colname = ["Patient1", "Patient2", "Patient1", "Patient2", "Patient3", "Patient4", "Patient5"]
       );

julia> using MultiAssayExperiments;

julia> out = MultiAssayExperiment(exp, cd, sm)
MultiAssayExperiment object
  experiments(2): foo bar
  sampledata(2): name disease
  metadata(0):
```
