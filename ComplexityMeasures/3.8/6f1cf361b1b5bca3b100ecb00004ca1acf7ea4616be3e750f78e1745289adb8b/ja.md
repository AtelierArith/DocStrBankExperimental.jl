```
Outcome <: Number
Outcome(num::Integer)
```

整数を表す未指定だが列挙された結果を表す便利なラッパーです。これは、一般的な結果（`counts`を使用する際に割り当てられる）と実際の整数結果（`counts_and_outcomes`を使用する際に割り当てられる可能性がある）を区別するために存在します。また、`Counts`や`Probabilities`の整形表示にも使用されます。
