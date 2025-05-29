```julia
hasresult(data::PLaplace.PLaplaceData) -> Bool

```

オブジェクトが結果を含んでいるかどうかを返します。つまり、アルゴリズムが実行され、収束したかどうかです。結果が `data.v` を介して使用される前に呼び出す必要があります。
