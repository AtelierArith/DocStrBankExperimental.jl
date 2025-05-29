```
@closure closure_expression
```

クロージャ定義 `closure_expression` を let ブロックでラップして、Julia コンパイラが改善された型情報を生成するように促します。例えば：

```julia
callfunc(f) = f()

function foo(n)
   for i=1:n
       if i >= n
           # 起こりにくいイベント - 速くなるはずです。しかし、クロージャ内での `i` のキャプチャは
           # Julia 0.6 コンパイラを混乱させ、変数 `i` をボックス化させるため、
           # `@closure` を削除すると 100 倍のパフォーマンス低下を引き起こします。
           callfunc(@closure ()->println("Hello $i"))
       end
   end
end
```

これは良いことではありません - これは、Julia 0.6 コンパイラによって推論される型情報のいくつかの非効率性に対するヒューリスティックな回避策です。しかし、クロージャを避けるためにコードを再構築する必要なく、多くのケースで大きなスピードアップをもたらす可能性があります。
