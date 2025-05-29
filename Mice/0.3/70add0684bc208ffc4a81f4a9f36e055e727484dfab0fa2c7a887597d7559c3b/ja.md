```
mice(
    data;
    m::Int = 5,
    imputeWhere::AxisVector{Vector{Bool}} = findMissings(data),
    visitSequence::Vector{String} = makeMonotoneSequence(imputeWhere),
    methods::AxisVector{String} = makeMethods(data),
    predictorMatrix::AxisMatrix{Int} = makePredictorMatrix(data),
    iter::Int = 10,
    progressReports::Bool = true,
    kwargs...
    )
```

データセット内の欠損値をMICEアルゴリズムを使用して補完します。出力は`Mids`オブジェクトです。

欠損値を含むデータ（`data`）は、`Tables.jl`テーブルとして提供する必要があります。

作成される補完の数は`m`で指定されます。

`imputeWhere`は、データを補完する場所を指定するブールベクトルの`AxisVector`です。デフォルトはすべての欠損データを補完することです。

変数は`visitSequence`で指定された順序で補完されます。デフォルトは欠損データの割合に基づいて昇順にソートされます。順序は、希望する順序の変数名のベクトルを使用してカスタマイズできます。全く補完しない列は、訪問シーケンスから省略できます。

各変数の補完方法は、`AxisVector` `methods`で指定されます。デフォルトはすべての変数に対して予測平均マッチング（`pmm`）を使用することです。補完しない変数は、空の文字列（""）を使用してそのようにマークできます。

予測子行列は、`AxisMatrix` `predictorMatrix`で指定されます。デフォルトは、各変数の予測子として他のすべての変数を使用することです。他の変数を予測しない変数は、行列内で0を使用してそのようにマークできます。

反復の数は`iter`で指定されます。

`progressReports`が`true`の場合、進行状況インジケーターがコンソールに表示されます。
