```
IMEXAlgorithm(tableau, newtons_method, [constraint])
IMEXAlgorithm(name, newtons_method, [constraint])
```

ODEを解くためのIMEXアルゴリズムを構築します。オプションの名前と制約があります。最初のコンストラクタは任意の`IMEXTableau`とオプションの制約を受け入れ、アルゴリズムに名前を付けません。2番目のコンストラクタは、アルゴリズム名からテーブルとデフォルトの制約を自動的に決定します。この名前は`IMEXARKAlgorithmName`でなければなりません。
