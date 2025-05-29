```
`SummarizedExperiment(assays, rowdata, coldata, metadata = Dict{String,Any}())`

提供されたアッセイと行/列の注釈を使用して、`SummarizedExperiment`のインスタンスを作成します。

`assays`のすべてのエントリは、最初の2つの次元の範囲が同じである必要があります。ただし、それ以外の次元は任意の数を持つことができます。各アッセイは異なる型であることができます。

`rowdata`の行数は、`assays`の各エントリの最初の次元の範囲と等しくなければなりません。同様に、`coldata`の行数も、2番目の次元の範囲と等しくなければなりません。いずれの場合も、最初の列は`"name"`と呼ばれ、`String`または`Nothing`の`Vector`を含む必要があります（名前が利用できない場合）。

`assays`は空であっても構いません。

# 例

```

jldoctest julia> using SummarizedExperiments

julia> assays = OrderedDict{String, AbstractArray}(           "foobar" => [[1,2] [3,4] [5,6]],            "whee" => [[1.2,2.3] [3.4,4.5] [5.6,7.8]]);

julia> rowdata = DataFrame(           name = [ "X", "Y" ],           type = ["protein", "transcript"]);

julia> coldata = DataFrame(           name = [ "a", "b", "c" ],           treatment = ["normal", "drug1", "drug2"]);

julia> x = SummarizedExperiment(assays, rowdata, coldata) 2x3 SummarizedExperiment   assays(2): foobar whee   rownames: X Y   rowdata(2): name type   colnames: a b c   coldata(2): name treatment   metadata(0): ```
