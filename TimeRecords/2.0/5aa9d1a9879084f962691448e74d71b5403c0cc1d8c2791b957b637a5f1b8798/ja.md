mapvalues!(f, ts::AbstractTimeSeries) -> ts

呼び出し可能な "f" を ts の各値にマッピングし、インプレースで変更します。出力は入力と同じ型でなければなりません。
