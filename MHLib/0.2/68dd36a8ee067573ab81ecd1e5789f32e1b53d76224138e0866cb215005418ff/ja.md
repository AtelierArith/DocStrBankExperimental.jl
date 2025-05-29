```
two_exchange_random_fill_neighborhood_search!(::SubsetVectorSolution, best_improvement)
```

2-交換近傍を検索し、ランダムな順序で`fillup!()`を続けます。

選択された各位置は、選択されていない位置と交換されることが試みられ、その後`fillup!()`が行われます。

近傍はランダム化された方法で検索されます。効率的な問題特有のデルタ評価のために、メソッド`element_removed_delta_eval`と`element_added_delta_eval`をオーバーロードします。解が改善できた場合はtrueを返し、そうでない場合は解は変更されません。
