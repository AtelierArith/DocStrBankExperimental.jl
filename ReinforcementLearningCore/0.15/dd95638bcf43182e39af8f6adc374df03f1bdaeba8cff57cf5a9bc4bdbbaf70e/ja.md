```
Agent(;policy, trajectory) <: AbstractPolicy
```

`AbstractPolicy`のラッパーです。一般的に言えば、異なるステージで軌跡とポリシーを適切に更新する以外は何もしません。AgentはCallableであり、その呼び出しメソッドはポリシーに渡される可変引数とキーワード引数を受け入れます。
