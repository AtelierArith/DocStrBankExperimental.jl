```
APIから識別子データを取得します。この関数は、`String`または[`Identifier`](@ref identifier_header)を受け入れます。

関連情報: [`makeidentifier`](@ref)、[`Identifier`s](@ref identifier_header)

識別子に`String`を使用する場合は、識別子タイプも渡す必要があります。すべての識別子が同じタイプである場合は、`String`を渡すことができます。そうでない場合は、識別子の`Vector`と同じ長さの`Vector`を渡してください。

この関数を識別子の`Vector`に対してブロードキャストしないでください。`Vector`を`ids`引数として渡します。キーとして[`Identifier`](@ref identifier_header)文字列を持つ`Dict`を返します。

キーワード引数はAPIクエリに渡され、1つ以上の以下のいずれかでなければなりません：

  * `micCode`
  * `currency`
  * `securityType2`
  * `securityType`
  * `stateCode`
  * `exchCode`
  * `marketSecDes`

詳細情報は[OpenFIGI API](https://www.openfigi.com/api#get-v3-mapping-values)のウェブサイトで入手できます。

`Vector`を`ids`に渡す場合、各`kwarg`は`String`または同じ長さの`Vector`である必要があります。

関連情報: [`OpenFigiAPI`](@ref)、[`OpenFigiAsset`](@ref)

# 例

```

jldoctest; setup = :(using FinancialSymbology) julia> identifiers = makeidentifier.(["AAPL US Equity", "BDDXSM4"]) 2-element Vector{Identifier}:  "AAPL US Equity"  "BDDXSM4"

julia> fetchsecuritydata(identifiers) Dict{String, StructArrays.StructArray} with 2 entries:   "AAPL US Equity" => FinancialSymbology.OpenFigiAsset[OpenFigiAsset…   "BDDXSM4"        => FinancialSymbology.OpenFigiAsset[OpenFigiAsset…

```

```

jldoctest; setup = :(using FinancialSymbology) julia> identifiers = [Ticker("AAPL US Equity"), Sedol("BDDXSM4")] 2-element Vector{Identifier}:  "AAPL US Equity"  "BDDXSM4"

julia> fetchsecuritydata(identifiers) Dict{String, StructArrays.StructArray} with 2 entries:   "AAPL US Equity" => FinancialSymbology.OpenFigiAsset[OpenFigiAsset…   "BDDXSM4"        => FinancialSymbology.OpenFigiAsset[OpenFigiAsset…

```

```

jldoctest; setup = :(using FinancialSymbology) julia> tickers = ["AAPL", "VOD", "TSLA"] 3-element Vector{String}:  "AAPL"  "VOD"  "TSLA"

julia> fetchsecuritydata(tickers, "TICKER"; marketSecDes="Equity", exchCode=["US", "LN", "US"]) Dict{String, StructArrays.StructArray} with 3 entries:   "AAPL" => FinancialSymbology.OpenFigiAsset[OpenFigiAsset…   "VOD"  => FinancialSymbology.OpenFigiAsset[OpenFigiAsset…   "TSLA" => FinancialSymbology.OpenFigiAsset[OpenFigiAsset…

```

```

jldoctest; setup = :(using FinancialSymbology) julia> idstrings = ["BBG000B9XRY4", "037833100", "US0378331005"] 3-element Vector{String}:  "BBG000B9XRY4"  "037833100"  "US0378331005"

julia> idtypes = ["ID*BB*GLOBAL", "ID*CUSIP", "ID*ISIN"] 3-element Vector{String}:  "ID*BB*GLOBAL"  "ID*CUSIP"  "ID*ISIN"

julia> fetchsecuritydata(idstrings, idtypes; exchCode="US") Dict{String, StructArrays.StructArray} with 3 entries:   "US0378331005" => FinancialSymbology.OpenFigiAsset[OpenFigiAsset…   "037833100"    => FinancialSymbology.OpenFigiAsset[OpenFigiAsset…   "BBG000B9XRY4" => FinancialSymbology.OpenFigiAsset[OpenFigiAsset…

```

```
