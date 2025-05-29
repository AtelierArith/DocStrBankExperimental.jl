```
BranchlengthSampler

加法提案関数を対数ドメインで指定し、枝長の対数に対する事前分布を指定できるタイプです。また、`acc_ratio`を格納しており、これは`(ratio, total, #acceptances)`のタプルで、`ratio::Float64`は受け入れ比率、`total::Int64`は提案の総数、`#acceptances::Int64`は受け入れの数です。
```
