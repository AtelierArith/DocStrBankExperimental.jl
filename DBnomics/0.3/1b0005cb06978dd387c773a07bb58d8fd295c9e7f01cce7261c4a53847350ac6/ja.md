```
rdb(
    provider_code::Union{Array, String, Nothing} = nothing,
    dataset_code::Union{String, Nothing} = nothing,
    mask_arg::Union{String, Nothing} = nothing;
    ids::Union{Array, String, Nothing} = nothing,
    dimensions::Union{Dict, NamedTuple, String, Nothing} = nothing,
    mask::Union{String, Nothing} = nothing,
    query::Union{String, Nothing} = nothing,
    api_link::Union{String, Nothing} = nothing,
    use_readlines::Bool = DBnomics.use_readlines,
    curl_config::Union{Nothing, Dict, NamedTuple} = DBnomics.curl_config,
    filters::Union{Nothing, Dict, Tuple} = DBnomics.filters,
    kwargs...
)
```

`rdb` は、`ids`、`dimensions`、`mask`、`query` などのショートカットや `api_link` を使用して、[DBnomics](https://db.nomics.world/) からデータシリーズをダウンロードします。

この関数は、[DBnomics](https://db.nomics.world/) から数億のデータシリーズにアクセスするためのものです。各シリーズのコードは [DBnomics](https://db.nomics.world/) のウェブサイトに記載されています。

ショートカット `ids` が使用される場合、引数名を省略でき、`ids` は `provider_code` を通じて渡されます。

引数 `api_link` のみが提供される場合、引数名を省略できます。文字列は直接 `api_link` に渡されます。

同様に、`provider_code`、`dataset_code`、`mask` のみが使用される場合、引数名を省略できます。`mask` は `mask_arg` を通じて渡されます。

デフォルトでは、関数は `DataFrame` を返します。

# 引数

  * `provider_code::Union{Array, String, Nothing} = nothing`: プロバイダーの DBnomics コード。
  * `dataset_code::Union{String, Nothing} = nothing`: データセットの DBnomics コード。
  * `mask_arg::Union{String, Nothing} = nothing`: 指定されたプロバイダーとデータセット内の1つまたは複数のマスクの DBnomics コード。引数名が指定されていない場合に使用されます。
  * `ids::Union{Array, String, Nothing} = nothing`: 1つまたは複数のシリーズの DBnomics コード。
  * `dimensions::Union{Dict, NamedTuple, String, Nothing} = nothing`: 指定されたプロバイダーとデータセット内の1つまたは複数の次元の DBnomics コード。`Dict` または `NamedTuple` の場合、関数 `json`（パッケージ **JSON.jl** から）が適用されて JSON オブジェクトが生成されます。
  * `mask::Union{String, Nothing} = nothing`: 指定されたプロバイダーとデータセット内の1つまたは複数のマスクの DBnomics コード。
  * `query::Union{String, Nothing} = nothing`: プロバイダーのデータセットからシリーズをフィルタリング/選択するためのクエリ。
  * `api_link::Union{String, Nothing} = nothing`: 検索の DBnomics API リンク。`http://` または `https://` で始まる必要があります。
  * `use_readlines::Bool = DBnomics.use_readlines`: （デフォルト `false`）`true` の場合、データは `readlines` 関数を使用して要求され、読み取られます。
  * `curl_config::Union{Nothing, Dict, NamedTuple} = DBnomics.curl_config`: （デフォルト `nothing`）`nothing` でない場合、プロキシ接続を構成するために使用されます。この構成は、パッケージ **HTTP.jl** の関数 `HTTP.get` または `HTTP.post` のキーワード引数に渡されます。
  * `filters::Union{Nothing, Dict, Tuple} = DBnomics.filters`: （デフォルト `nothing`）この引数は、サーバーにリクエストを送信する前にパッケージ **JSON.jl** の関数 `json` が使用されるため、1つのフィルタ用の `Dict` である必要があります。複数のフィルタの場合、有効なフィルタの `Tuple` を提供する必要があります（例を参照）。有効なフィルタは、キー `code` の値が文字列であり、キー `parameters` の値が `frequency` と `method` または `nothing` を持つ `Dict` です。
  * `kwargs...`: `HTTP.get` または `HTTP.post` に渡されるキーワード引数。

# 例

```jldoctest
## By ids
julia> df1 = rdb(ids = "AMECO/ZUTN/EA19.1.0.0.0.ZUTN");
# or
julia> df1 = rdb("AMECO/ZUTN/EA19.1.0.0.0.ZUTN");

julia> df2 = rdb(ids = ["AMECO/ZUTN/EA19.1.0.0.0.ZUTN", "AMECO/ZUTN/DNK.1.0.0.0.ZUTN"]);

julia> df3 = rdb(ids = ["AMECO/ZUTN/EA19.1.0.0.0.ZUTN", "IMF/BOP/A.FR.BCA_BP6_EUR"]);


## By dimensions
julia> df1 = rdb("AMECO", "ZUTN", dimensions = Dict(:geo => "ea12"));
# or
julia> df1 = rdb("AMECO", "ZUTN", dimensions = (geo = "ea12",));

julia> df2 = rdb("AMECO", "ZUTN", dimensions = Dict(:geo => ["ea12", "dnk"]));
# or
julia> df2 = rdb("AMECO", "ZUTN", dimensions = (geo = ["ea12", "dnk"],));

julia> dim = Dict(:country => ["DZ", "PE"], :indicator => ["ENF.CONT.COEN.COST.ZS", "IC.REG.COST.PC.FE.ZS"]);
julia> df3 = rdb("WB", "DB", dimensions = dim);
# or
julia> dim = (country = ["DZ", "PE"], indicator = ["ENF.CONT.COEN.COST.ZS", "IC.REG.COST.PC.FE.ZS"]);
julia> df3 = rdb("WB", "DB", dimensions = dim);


## By mask
julia> df1 = rdb("IMF", "BOP", mask = "A.FR.BCA_BP6_EUR");
# or
julia> df1 = rdb("IMF", "BOP", "A.FR.BCA_BP6_EUR");

julia> df2 = rdb("IMF", "BOP", mask = "A.FR+ES.BCA_BP6_EUR");

julia> df3 = rdb("IMF", "BOP", mask = "A..BCA_BP6_EUR");

julia> df4 = rdb("IMF", "BOP", mask = "A.FR.BCA_BP6_EUR+IA_BP6_EUR");


## By query
julia> df1 = rdb("IMF", "WEO:2019-10", query = "France current account balance percent");

julia> df2 = rdb("IMF", "WEO:2019-10", query = "current account balance percent");


## By api_link
julia> df1 = rdb(api_link = "https://api.db.nomics.world/v22/series/WB/DB?dimensions=%7B%22indicator%22%3A%5B%22IC.REG.PROC.FE.NO%22%5D%7D&q=Doing%20Business&observations=1&format=json&align_periods=1&offset=0&facets=0");
# or
julia> df2 = rdb("https://api.db.nomics.world/v22/series/WB/DB?dimensions=%7B%22indicator%22%3A%5B%22IC.REG.PROC.FE.NO%22%5D%7D&q=Doing%20Business&observations=1&format=json&align_periods=1&offset=0&facets=0");


## Use proxy with curl
julia> h = Dict(:proxy => "http://<proxy>:<port>");

julia> DBnomics.options("curl_config", h);
julia> df1 = rdb(ids = "AMECO/ZUTN/EA19.1.0.0.0.ZUTN");
# or
julia> df1 = rdb(ids = "AMECO/ZUTN/EA19.1.0.0.0.ZUTN", curl_config = h);

# Regarding the functioning of HTTP.jl, you might need to modify another option
# It will change the url from https:// to http://
# (https://github.com/JuliaWeb/HTTP.jl/pull/390)
julia> DBnomics.options("secure", false);


## Use readlines and download
julia> DBnomics.options("use_readlines", true);
julia> df1 = rdb(ids = "AMECO/ZUTN/EA19.1.0.0.0.ZUTN");
# or
julia> df1 = rdb(ids = "AMECO/ZUTN/EA19.1.0.0.0.ZUTN", use_readlines = true);


## Apply a filter to the series
# One filter
julia> filters = Dict(:code => "interpolate", :parameters => Dict(:frequency => "daily", :method => "spline"));
julia> df1 = rdb(ids = ["IMF/WEO:2019-10/ABW.BCA.us_dollars", "IMF/WEO:2019-10/ABW.NGDPD.us_dollars"], filters = filters);

# For two filters
julia> filter1 = Dict(:code => "interpolate", :parameters => Dict(:frequency => "quarterly", :method => "spline"));
julia> filter2 = Dict(:code => "aggregate", :parameters => Dict(:frequency => "annual", :method => "average"));
julia> filters = (filter1, filter2);
julia> df1 = rdb(ids = ["IMF/WEO:2019-10/ABW.BCA.us_dollars", "IMF/WEO:2019-10/ABW.NGDPD.us_dollars"], filters = filters);

julia> filter1 = Dict(:code => "interpolate", :parameters => Dict(:frequency => "monthly", :method => "linear"));
julia> filter2 = Dict(:code => "x13", :parameters => nothing);
julia> filters = (filter1, filter2);
julia> df1 = rdb("ECB/EXR/A.AUD.EUR.SP00.A", filters = filters);
```
