```
update_fitness!([f], eval::Evaluator, candidate::Candidate; force::Bool=false) -> Candidate
```

`candidate`のフィットネスを計算し、オプションで`f`を適用します。`force`は、候補者がすでに非NAのフィットネスを持っている場合に、フィットネスを再評価するかどうかを指定します。
