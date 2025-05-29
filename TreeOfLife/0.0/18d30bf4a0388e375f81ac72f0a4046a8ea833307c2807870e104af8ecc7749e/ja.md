```
getconsensus(trees::Vector{<:AbstractTree}; 
	threshold::Float64=0.5, every::Int=0) :: CladoTree
```

系統樹を要約して、支持率が閾値以上のクレードのみがコンセンサスツリーに残るようにします。

引数 `threshold` は `0.5` と `1.0` の間の数値である必要があります。デフォルト値は `0.5` です。

引数 `every` は正の整数に設定されている場合、（おそらく長い）分析プロセスが `every` 本の木ごとにログを出力します。デフォルト値は `0` です。
