```
prepare_probe(outcome_data::DataFrame; layer::Int=24, value_var::Symbol=:value)
```

線形プローブのためのデータを準備します。`outcome_data`は`sentence_id`列を持つ`DataFrame`である必要があり、この列にはユニークな値が含まれている必要があります。また、結果変数を含む列も必要です。デフォルトでは、この列は`value`と呼ばれると仮定されますが、`value_var`引数を使用して変更することができます。`layer`引数は、プローブに使用するレイヤーを示します。デフォルトは最後のレイヤー（24）です。
