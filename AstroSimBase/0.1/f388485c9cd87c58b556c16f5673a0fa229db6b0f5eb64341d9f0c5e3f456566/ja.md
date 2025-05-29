function randin(T, a, b) function randin(a, b)

`[a,b]`の範囲で一様な乱数を生成します。`a`と`b`が`Unitful.Quantity`である場合の`rand(a:b)`からのエラーを回避します。
