get_value(d::LoopCategory, n::Int, colname::Symbol)

`d`のキーdatanamesの`colname`に対する行`n`に対応する値を返します。`colname`が子カテゴリに属する場合、一般的には`colname[n]`にはなりません。代わりに、キーdatanamesの値を使用して正しい値を検索します。
