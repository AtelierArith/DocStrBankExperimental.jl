```
MultiAssayExperiment(experiments, sampledata, samplemap, metadata = Dict{String,Any}())
```

Creates a new `MultiAssayExperiment` from its components.

`experiments` should contain ordered pairs of experiment names and `SummarizedExperiment` objects. Each `SummarizedExperiment` may contain any number and identity for the rows. However, the column names must be non-nothing and unique within each object.

Each row of `sampledata` corresponds to a conceptual sample. The first column should be called `name` and contain the names of the samples in a `Vector{String}`. Sample names are arbitrary but should be unique. Any number and type of other columns may be provided, usually containing sample-level annotations.

The `samplemap` table is expected to have 3 `Vector{String}` columns - `sample`, `experiment` and `colname` - specifying the correspondence between each conceptual sample and the columns of a particular `SummarizedExperiment`. See [`setsamplemap!`](@ref) for more details on the expected format.

Note that values in the `samplemap` columns need not have a 1:1 match to their cross-referenced target;  any values unique to one or the other will be ignored in methods like [`expandsampledata`](@ref) and [`filtersamplemap`](@ref). This allows users to flexibly manipulate the object without constantly hitting validity checks.

The `metadata` stores other annotations unrelated to the samples.

# Examples

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
