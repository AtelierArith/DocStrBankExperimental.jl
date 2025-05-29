FitInput(parameters::Dict{String,Any},              dependent::Vector{TimeSeries{T}},             exogenous::Vector{TimeSeries{T}}) where T

FitInputは、フィット関数に必要な唯一の情報です。フィット関数は、依存変数、外生変数、およびパラメータを使用します。データセットではないフィット関数に渡されるすべての追加情報は、parameters Dictの中に含める必要があります。また、辞書の中に'args'および'kwargs'のキーを含めることができ、これらはフィット関数に直接渡されます。
