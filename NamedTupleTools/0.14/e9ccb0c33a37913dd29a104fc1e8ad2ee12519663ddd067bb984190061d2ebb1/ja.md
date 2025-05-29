```
merge_recursive(nt1, nt2)
merge_recursive(nt1, nt2, nt3, ..)
```

名前付きタプルを再帰的にマージします。名前付きタプルの引数のうち、同じフィールド名（同じキー）を共有するものが複数ある場合、右側の引数のキーの値が伝播されます。各名前付きタプルが異なるフィールド名（キー）を持つ場合、すべての名前付きフィールドがそれぞれの値と共に集められます。名前付きフィールドは、出現した順序（右側の引数、次に右側の引数、..、次に左側の引数、左側の引数）で表示されます。

ネストされた名前付きタプルがない場合、`merge(nt1, nts..., recursive=true)`は`merge(nt1, nts...)`と同じです。

```
a = (food = (fruits = (orange = "mango", white = "pear"),
             liquids = (water = "still", wine = "burgandy")))

b = (food = (fruits = (yellow = "banana", orange = "papaya"),
             liquids = (water = "sparkling", wine = "champagne"),
             bread = "multigrain"))

merge(b,a)  == (fruits  = (orange = "mango", white = "pear"),
                liquids = (water = "still", wine = "burgandy"),
                bread   = "multigrain")

merge_recursive(b,a) ==
               (fruits  = (yellow = "banana", orange = "mango", white = "pear"),
                liquids = (water = "still", wine = "burgandy"),
                bread   = "multigrain")

merge(a,b)  == (fruits  = (yellow = "banana", orange = "papaya"),
                liquids = (water = "sparkling", wine = "champagne"),
                bread   = "multigrain")

merge_recursive(a,b) ==
               (fruits  = (orange = "papaya", white = "pear", yellow = "banana"),
                liquids = (water = "sparkling", wine = "champagne"),
                bread   = "multigrain")
```

参照: [`merge`](@ref)
